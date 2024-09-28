<template>
      <loader v-if="loading" />
      <error-message v-if="ErrorTextDescription" :errorText="errorTextDescription" />
      <div v-if="!id" class="nodata">
        <h1>Выберите пост для получения полной информации о нем</h1>
      </div>
      <div v-if="id" class="post-wrapper">
        <div class="post">
          <h1>post title</h1>
          <div class="post-data">
            <span> postData</span>
            <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ea porro voluptatibus dolore? Illum veniam blanditiis incidunt quis sed eum nesciunt ducimus beatae, laborum accusamus magnam ab odit. Consequuntur numquam totam provident vitae quos animi enim dicta quae perferendis pariatur, sunt eligendi facilis ut nobis, sit aspernatur quaerat nihil consequatur in dolorem. Neque aspernatur error commodi ullam recusandae doloribus tempore sequi sunt in quasi ipsam necessitatibus accusamus, quae voluptate. Laborum, sapiente saepe rerum voluptatem repellendus sit autem ex eos aperiam quae molestiae esse facilis at amet nemo corrupti repellat. Fuga facilis tenetur facere fugiat quas quia voluptatum id, possimus dolor odio.</p>
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
            ErrorTextDescription:'',

            
        }

    },
    props:{
        id:String
    },

    methods:{
        
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