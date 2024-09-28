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
          
        </div>
          {{ id }}
      </div>
</template>
<script>
import Loader from './ui/Loader.vue'
import ErrorMessage from './ui/ErrorMessage.vue'


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

  },
}
</script>
<style lang="scss" scoped>
  .post-wrapper{
    padding:20px 
  }
  .post-data{
    display: grid;
    grid-template-columns: 100px 1fr;
    padding-top: 20px;
  }
</style>