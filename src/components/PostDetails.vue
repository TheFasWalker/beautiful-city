<template>
      <loader v-if="loading" />
      <error-message v-if="errorTextDescription" :errorText="errorTextDescription" />
      <div v-if="!id" class="nodata">
        <h1>Выберите пост для получения полной информации о нем</h1>
      </div>
      <div v-if="id" class="post-wrapper">
        <div class="post">
          <h1>{{ postData.title }}</h1>
          <div class="post-data">
            <span> postData</span>
            <p>{{ postData.body }}</p>
          </div>
        </div>
        <div class="postComments">
    <PostComment/>
    <PostComment/>
    <PostComment/>
    <PostComment/>
    <PostComment/>
    <PostComment/>
    <PostComment/>
    <PostComment/>
    <PostComment/>

        </div>
          {{ id }}
      </div>
</template>
<script>
import Loader from './ui/Loader.vue'
import ErrorMessage from './ui/ErrorMessage.vue'
import Comment from './Comment.vue'


export default{
    data(){
        return {
            loading:false,
            errorTextDescription:'',
            postData:{}

            
        }

    },
    props:{
        id:Number
    },
    methods:{
      getPostData:async function(){
        console.log('Fetching post data for ID:', this.id);
        try{
          console.log('try')
          this.loading = true

          this.errorTextDescription = ''
          console.log(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
          const response = await fetch (`https://jsonplaceholder.typicode.com/posts/${this.id}`)

          if (!response.ok) {

            throw new Error('Network response was not ok')

          }
          this.postData = await response.json()

          console.log(this.postData)
        }catch(error){
          this.errorTextDescription = 'Error fetching post data: ' + error.message
          this.loading=false
        }finally {
        this.loading = false
        this.errorTextDescription = ''
      }     
      }      
    },
    watch: {
    id: {
      immediate: true, 
      handler(newId) {
        if (newId) {
          this.getPostData();
        }
      }
    }
  },

    components: {
    loader: Loader,
    ErrorMessage: ErrorMessage,
    PostComment:Comment

  },
}
</script>
<style lang="scss" scoped>
  .post-wrapper{
    padding:20px ;
    display: grid;
    grid-template-rows: 200px 1fr;
    height: 100%;
  }
  .post-data{
    display: grid;
    grid-template-columns: 100px 1fr;
    padding-top: 20px;
  }
  .postComments{
    display: flex;
    flex-direction: column;
    gap: 5px;
    overflow-y: auto;
    box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
    border-radius: 10px;
  }
</style>