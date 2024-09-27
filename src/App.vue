

<script>

import ErrorMessage from './components/ui/ErrorMessage.vue';
import Loader from './components/ui/Loader.vue';

export default {
data(){
  return{
    loading:false,
    postData:[],
    errorTextDescription:''
  }
},
  components: {
    loader:Loader,
    ErrorMessage:ErrorMessage,
  },
  mounted(){
    this.getPosts();
  },
  methods:{
    getPosts: async function(){
      try{
        this.loading = true
        this.error = ''
        const response = await fetch('https://jsonplaceholder.typicode.com/postss123123/')
      if (!response.ok) {
          throw new Error('Network response was not ok')
        }
        this.postData = await response.json()
        console.log(this.postData)
    }catch(error){
      this.errorTextDescription='Error fetching posts: ' + error.message
      console.log('asdf')
    } finally {
        this.loading = false
        this.error = ''
      }

    }
  }
}
;
</script>
  <style lang="scss" >
    .header{
      display: flex;
      flex-direction: row;
      align-items: center;
      gap: 20px;
      width: 100%;
      padding: 10px 0;
    }
    .main{
      width: 100%;
      // height: 100%;
      min-height: 250px;
      max-height: 700px;
      background-color: green;
      position: relative;
    }
  </style>
<template>
  <div class="header">
    <h1>Приложение для просмотра постов с </h1>
    <a href="https://jsonplaceholder.typicode.com/" target="_blank">jsonplaceholder.typicode.com</a>
  </div>
  <div class="main">
    <loader v-if="loading"/>
    <error-message v-if="errorTextDescription"
    :errorText="errorTextDescription"/>
  </div>
</template>

