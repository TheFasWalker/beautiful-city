<script>

import ErrorMessage from './components/ui/ErrorMessage.vue';
import Loader from './components/ui/Loader.vue';
import PostPreview from './components/PostPreview.vue'

export default {
  data() {
    return {
      loading: false,
      postData: [],
      errorTextDescription: '',
      postDataLoading: false,
      postErrorTextDescription: '',
      postData:[]
    }
  },
  components: {
    loader: Loader,
    ErrorMessage: ErrorMessage,
    PostPreview: PostPreview
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
        this.error = ''
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
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.nodata{

  width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
<template>

  <div class="header">
    <h1>Приложение для просмотра постов с </h1>
    <a href="https://jsonplaceholder.typicode.com/" target="_blank">jsonplaceholder.typicode.com</a>
  </div>
  <div class="main">
    <div class="sidebar">
      <loader v-if="loading" />
      <error-message v-if="errorTextDescription" :errorText="errorTextDescription" />
      <PostPreview
        v-for="post of postData"
        :title="post.title"
        :id="post.id"
      />
    </div>
    <div class="content">
      <loader v-if="postDataLoading" />
      <error-message v-if="postErrorTextDescription" :errorText="errorTextDescription" />
      <div v-if="!postData" class="nodata">
        <h1>Выберите пост для получения полной информации о нем</h1>
      </div>
    </div>


  </div>
</template>
