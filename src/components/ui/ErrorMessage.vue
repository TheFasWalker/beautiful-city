<template>
   <div class="errorWrapper">
    <h1>{{ errorText }}</h1>
   </div>
</template>
<script>
export default{
    props:{
        errorText:{
      type: String,
      required: true
    }
    }
}
</script>
<style lang="scss" scoped>
.errorWrapper{
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 999;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgb(255 0 0 / 72%);
}
</style>