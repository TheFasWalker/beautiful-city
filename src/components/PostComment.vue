<template>
    <div class="comment">
        <div class="header">
            <span class="username"> {{ username }}</span>
            <button @click="getUserData">UserData</button>
        </div>

        <p>{{ body }}</p>
        <div class="userData" v-if="popupState">
            <div class="userData-wrapper" >
                <loader v-if="userDataLoading"/>
                <errorMessages v-if="errorMessage" :errorText="errorMessage"/>
                <button @click="closeUserPopup">close</button>
                <div class="userData-found" v-if="this.userData[0]">
                    <div class="userData-item" >
                        <span>username:</span>
                        <span>{{ this.userData[0].name }}</span>
                    </div>
                    <div class="userData-item">
                        <span>useremail:</span>
                        <span>{{ this.userData[0].email }}</span>
                    </div>
                    <div class="userData-item">
                        <span>companyName:</span>
                        <span v-if="this.userData[0].company.name">{{ this.userData[0].company.name }}</span>
                    </div>
                    <div class="userData-item">
                        <span>UserWebsite:</span>
                        <span >{{ this.userData[0].website }}</span>
                    </div>
                </div>
                <div class="userData-notfound">
                    данные пользователя не найдены
                </div>


            </div>

        </div>
    </div>
</template>
<script>
import Loader from './ui/Loader.vue';
import ErrorMessage from './ui/ErrorMessage.vue';

export default {
    data() {
        return {
            popupState: false,
            userDataLoading: false,
            errorMessage: '',
            userData: {}
    }
},
    props: {
        username: String,
        body: String.appl,
        email: String,
    },
    methods: {
        getUserData: async function () {

            try {
                this.userDataLoading = true
                this.errorMessage = ''

                const response = await fetch(`https://jsonplaceholder.typicode.com/users?email=${this.email}`)

                if (!response.ok) {
                    throw new Error('Network response was not ok')
                }

                this.userData = await response.json()

            } catch (error) {
                this.errorMessage = 'Error fetching post data: ' + error.message
                this.userDataLoading= false
            } finally {
                this.userDataLoading = false
                 this.errorMessage = ''
            }
            this.popupState = !this.popupState

        },
        closeUserPopup: function () {
            this.popupState = !this.popupState


        }
    },
    components: {
        loader: Loader,
        errorMessage:ErrorMessage
    }
}
</script>
<style lang="scss" scoped>
    .comment{
        border: 2px solid rgb(34, 185, 34);
        border-radius: 10px;
        padding: 20px 30px;
        position: relative;
    }
    .username{
        font-size: 25px;
        font-weight: 700;
    }
    .header{
        display: flex ;
        flex-direction: row;
        justify-content: space-between;
    }
    .userData-wrapper{
        position: relative;
    }
    .userData{
        position: absolute;
        top: 0;
        right: 0;
        padding: 20px 10px ;
        background-color: #ffffff;
        box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
        border-radius: 10px;
        z-index: 10;
        display: flex;
        flex-direction: column;
        gap: 5px;
        span:first-child{
            font-size: 18px;
            font-weight: 600;
        }
    }

</style>