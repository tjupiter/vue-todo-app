<template>
     
    <!-- <button 
    class="border border-green-900 rounded-full bg-green-500 hover:bg-green-400 text-white py-1 px-2"
    :style="{ background: color }">{{text}}</button>  -->

    <button 
    class="border rounded-full text-white py-2 px-4 shadow font-bold focus:outline-none "
    :class="tailwindColor"
    @click="onClick()">{{text}}</button> 

</template>

<script>


export default {
    name: 'Button',

    props: {
      text: String,
      color: String,
      tailwindColor: String
  },

  methods: {
      onClick() {
          this.$emit('btn-click')
      }
  }
}
</script>
