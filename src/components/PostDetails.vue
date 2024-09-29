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
          <PostComment
          v-for="comment of commentsData"
          :username="comment.name"
          :body="comment.body"
          :email="comment.email"/>


        </div>
          {{ id }}
      </div>
</template>
<script>
import Loader from './ui/Loader.vue'
import ErrorMessage from './ui/ErrorMessage.vue'
import Comment from './PostComment.vue'


export default{
    data(){
        return {
            loading:false,
          errorTextDescription: '',
          loadingConmments: false,
            errorCommentsLoading:'',
          postData: {},
            commentsData:[]


        }

    },
    props:{
        id:Number
    },
    methods:{
      getPostData:async function(){
        try{
          this.loading = true
          this.errorTextDescription = ''
          const response = await fetch (`https://jsonplaceholder.typicode.com/posts/${this.id}`)
          if (!response.ok) {
            throw new Error('Network response was not ok')
          }
          this.postData = await response.json()

        }catch(error){
          this.errorTextDescription = 'Error fetching post data: ' + error.message
          this.loading=false
        }finally {
        this.loading = false
        this.errorTextDescription = ''
        }
      },
      getPostComments: async function() {
        try {
          this.loadingConmments = true
          this.errorCommentsLoading = ''
            const response = await fetch (`https://jsonplaceholder.typicode.com/posts/${this.id}/comments`)
          if (!response.ok) {
            throw new Error('Network response was not ok');
          }
            this.commentsData = await response.json()
        } catch (error) {
          this.loadingConmments = false
            this.errerrorCommentsLoading = 'Error fetching post comments data: ' + error.message
        } finally {
          this.loadingConmments = false
          this.errorCommentsLoading = ''
        }
      }
    },
    watch: {
      id: {
        immediate: true,
        handler(newId) {
          if (newId) {
            this.getPostData();
            this.getPostComments()
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