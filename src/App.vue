<script>

import ErrorMessage from './components/ui/ErrorMessage.vue';
import Loader from './components/ui/Loader.vue';
import PostPreview from './components/PostPreview.vue'
import PostDetails from './components/PostDetails.vue'
import SearchInput from './components/ui/SearchInput.vue';


export default {
  data() {
    return {
      loading: false,
      postData: [],
      errorTextDescription: '',
      postData:[],
      activePostId:''
    }
  },
  components: {
    loader: Loader,
    ErrorMessage: ErrorMessage,
    PostPreview: PostPreview,
    PostDetails: PostDetails,
    SearchInput:SearchInput
  },
  mounted() {
    this.getPosts();
  },
  methods: {
    getPosts: async function () {
      try {
        this.loading = true
        this.error = ''
        const response = await fetch('https://jsonplaceholder.typicode.com/posts/')
        if (!response.ok) {
          throw new Error('Network response was not ok')
        }
        this.postData = await response.json()
        console.log(this.postData)
      } catch (error) {
        this.errorTextDescription = 'Error fetching posts: ' + error.message
        console.log('asdf')
      } finally {
        this.loading = false
        this.errorTextDescription = ''
      }

    }
  }
}
  ;
</script>
<style lang="scss">
.header {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 20px;
  width: 100%;
  padding: 10px 0;
}

.main {
  width: 100%;
  min-height: 250px;
  position: relative;

  display: grid;
  grid-template-columns: 400px 1fr;
}

.sidebar,
.content {
  height: 100%;
  overflow-y: auto;
  position: relative;
}
.sidebar{
  display: grid;
  grid-template-rows: 50px 1fr;
  gap: 10px;
}
.nodata{

  width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
}
.sidebar-results{
  display: flex;
  flex-direction: column;
  gap: 5px;
  height: 100%;
  overflow-y: scroll;
}
</style>
<template>

  <div class="header">
    <h1>Приложение для просмотра постов с </h1>
    <a href="https://jsonplaceholder.typicode.com/" target="_blank">jsonplaceholder.typicode.com</a>
  </div>
  <div class="main">
    <div class="sidebar">

      <SearchInput/>
      <loader v-if="loading" />
      <error-message v-if="errorTextDescription" :errorText="errorTextDescription" />
      <div class="sidebar-results">
        <PostPreview
        v-for="post of postData"
        :title="post.title"
        :key="post.id"
        @click="activePostId = post.id"
      />
      </div>

    </div>
    <div class="content" >

      <PostDetails :id="activePostId"/>
    </div>


  </div>
</template>
