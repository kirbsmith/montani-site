<template>
  <h2 class="text-5xl p-12 font-thin text-center">Shade Selection</h2>
  <div class="flex flex-row flex-wrap justify-center">
    <div v-for="shade in shades" :key="shade.id" class="flex flex-col items-center border-2 border-blue-900 p-6 m-6 rounded-xl">
      <img :src=getImgUrl(shade.image) alt="" class="w-64"/>
      <h3 class="py-2 text-2xl">{{ shade.name }}</h3>
      <p class="text-lg">${{ shade.price }}.00 per square foot</p>
      <ChoiceDisplay />
      <p v-if="!shadeDisplay">test</p>
      <p v-else>shade selection hidden</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ChoiceDisplay from '../components/shadeFabricDisplay.vue'

export default defineComponent({
  components: {
    ChoiceDisplay
  },

  data(){
    return {
      shades: [],
      shadeDisplay: false
    }
  },

  methods: {
    getImgUrl: function (img : string) {
      return require('@/images/' + img)
    }
  },

  mounted(){
    fetch('http://localhost:3000/shades')
      .then((res) => res.json())
      .then(data => this.shades = data)
      .catch(err => console.log(err.message))
  }
});
</script>
