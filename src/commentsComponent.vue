<template>
<div class="users">
    <loader v-if="loading"/>
    <error v-if="error" :errorText="error" />
    <div class="header">
        <h1>Приложение для просмотра пользователей с </h1>
    <a href="https://jsonplaceholder.typicode.com/" target="_blank">jsonplaceholder.typicode.com</a>
  </div>

    <div class="users-data">
    <userPreview v-for="user of usersData"
    key="user.id"
    :userData="user"/>
</div>
</div>
</template>

<script>
import Loader from './components/ui/Loader.vue'
import ErrorMessage from './components/ui/ErrorMessage.vue';
import userPreview from './components/userPreview.vue'


export default {
    data() {
        return {
            usersData: [],
            loading: false,
            error:''
        }
    },
    mounted() {
        this.getUsersData()
    },
    components: {
        loader: Loader,
        error: ErrorMessage,
        userPreview:userPreview
    },

    methods: {
        getUsersData: async function () {
            try {
                this.loading = true
                this.error = ''
                const response = await fetch('https://jsonplaceholder.typicode.com/users')
                if (!response.ok) {
                    throw new Error('Network response was not ok')
                }
                this.usersData = await response.json()
            } catch (error) {
                this.error= 'Error fetching users: ' + error.message
            } finally {
                this.loading = false
                this.error=''
            }
            console.log(this.usersData)
        }
    }
}
</script>
<style lang="scss" scoped>
.users{
    position: relative
}
.header {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 20px;
  width: 100%;
  padding: 10px 0;
}
.users-data{
    display: flex;
    flex-direction: column;
    gap: 10px;
}
</style>