<template>
  <div>
    <Index/>
  </div>
</template>

<script>
import Index from "./components/index.vue";
export default {
  name: 'App',
  components: {
    Index,
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
    font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif
  }
  body{
    padding:0;
    margin:0;
  }
</style>
