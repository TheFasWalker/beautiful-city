<template>
    <div class="comment">
        <div class="header">
            <span class="username"> {{ username }}</span>
            <button @click="getUserData">UserData</button>
        </div>

        <p>{{ body }}</p>
        <div class="userData" v-if="popupState">
            <button @click="closeUserPopup">close</button>
            <div class="userData-item">
                <span>username:</span>
                <span>UserName</span>
            </div>
            <div class="userData-item">
                <span>useremail:</span>
                <span>useremail@email.email</span>
            </div>
            <div class="userData-item">
                <span>companyName:</span>
                <span>useremail@email.email</span>
            </div>
            <div class="userData-item">
                <span>UserWebsite:</span>
                <span>useremail@email.email</span>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            popupState:false
    }
},
    props: {
        username: String,
        body: String.appl,
        email: String,
    },
    methods: {
        getUserData: function () {
            console.log(this.email)
            this.popupState = !this.popupState

        },
        closeUserPopup: function () {
            this.popupState = !this.popupState
        }
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