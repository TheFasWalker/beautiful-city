<template>
      <loader v-if="loading" />
      <error-message v-if="ErrorTextDescription" :errorText="errorTextDescription" />
      <div v-if="!id" class="nodata">
        <h1>Выберите пост для получения полной информации о нем</h1>
      </div>
      <div class="">
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
</style>