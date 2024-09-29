<script>
import firstComponent from './postComponenr.vue';
import secondComponent from './commentsComponent.vue';

export default {

  data() {
    return {
      state:'second'
    }

    },
      components:{
        firstComponent: firstComponent,
        secondComponent:secondComponent
  },
  methods: {

      }


}
  ;
</script>

<template>
  <div class="buttonsWrapper">
    <button @click="this.state='first'">работа с постами</button>
    <button @click="this.state='second'">второй компонент</button>
  </div>
<firstComponent v-if="this.state == 'first'"/>
<secondComponent v-if="this.state == 'second'" />
</template>

<style lang="scss" scoped>
.buttonsWrapper{
  position:fixed;
  background-color: gray;
  padding: 10px;
  top: 0;
  right: 0;
  z-index: 999;
  button{
    background-color: gainsboro;
    padding: 10px;
    cursor: pointer;
  }
}
</style>