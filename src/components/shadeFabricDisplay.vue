<template>
    <button @click="getChoices(); count++">
        You clicked me {{ count }} times.
    </button>
    <div class="flex flex-col text-center">
        <p v-if="shadeDisplay">please work</p>
        <p v-else>eh</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            choices: [],
            count: 0,
            shadeDisplay: false
        }
    },

    methods: {
        getChoices: function (){
        this.shadeDisplay = !this.shadeDisplay
        console.log(this.shadeDisplay)
    } 
    },

    mounted(){
    fetch('http://localhost:3000/shades')
      .then((res) => res.json())
      .then(data => this.choices = data)
      .catch(err => console.log(err.message))
  }
}
</script>