<script>
import firstComponent from './postComponenr.vue';
import secondComponent from './commentsComponent.vue';

export default {

  data() {
    return {
      state:''
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
<div class="main-item" v-if="!this.state">
<h1>Тестовое задание Красивый город</h1>
<br>
<p>К сожалению я несмог выполнить тестовое задание  как таковое(то что указано в самом ТЗ). - Само ТЗ есть в файле readme.md<br>
  Сделал максимальную реализацию работы с элементами. <br>
  В блоке работы с постами можно произвести поиск по "названию поста"<br>
  Редактирование данных не делал , так как я еще не затрагивал тему стейтменеджеров, а по хорошему это нужно делать с их помощью<br>
  Тему роутинга я тоже не затронул ибо во vue с этим пока не работал <br>
  P.S.  на данный момент работаю с vue только в роли человека, который делает мелкие правки по контенту и по стилям...
<br>
  У меня уже запланировано углубленное изучение vue3 ( начало 31.10)
  <br>
  <br>
  <h1>Спасибо за потраченное время!</h1>
</p>
</div>
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
.main-item{
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  height: 100vh;

}
</style>