<template>
  <div class="d-flex" style="justify-content: center">
    <input type="text"   class="form-control" @input="onInput">
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods:{
    onInput:function (even){
      this.$emit('termChange' , even.target.value);
    }
  }
}
</script>

<style scoped>
input{
  width: 75%;
}
div{
  text-align: center;
  margin: 20px;
}
</style>