<template>
    <div class="user-wrapper">
        <div class="user-item">
            <span>UserName: </span>
            <span>{{ userData.name }}</span>
        </div>
        <div class="user-item">
            <span>userEmail: </span>
            <a href="mailto:{{ userData.email }}">{{ userData.email }}</a>

        </div>
        <div class="user-item">
            <span>userCompany: </span>
            {{ userData.company.name }}
        </div>
        <button @click="showData = !showData">Показать дополнительные данные</button>
        <div class="user-hidden" v-show="showData">
            <div class="user-elem">
                <div class="user-item">
                    <span>city:</span>
                    <span>{{ userData.address.city }}</span>
                </div>
                <div class="user-item">
                    <span>suite:</span>
                    <span>{{ userData.address.suite }}</span>
                </div>
                <div class="user-item">
                    <span>zipcode:</span>
                    <span>{{ userData.address.city }}</span>
                </div>
                <div class="user-item">
                    <span>city:</span>
                    <span>{{ userData.address.zipcode }}</span>
                </div>
            </div>
            <div class="user-elem">
                <div class="user-item">
                    <span>UserPhone:</span>
                    <a href="tel:{{ userData.phone }}">{{ userData.phone }}</a>
                </div>

                <div class="user-item">
                    <span>UserWebsite:</span>
                    <a href="tel:{{ userData.website }}">{{ userData.website }}</a>
                </div>
            </div>
        </div>

</div>
</template>
<script>
export default {
    data() {
        return {
            showData:false
        }
    },
    props: {
        userData:Array
    }
}
</script>
<style lang="scss" scoped>
.user-item {

    span:first-child{
        font-weight: 700;
    }
}
.user-wrapper{
    box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
    padding: 20px 10px;
}
    .user-hidden{
        display: grid;
        grid-template-columns:  1fr 1fr 1fr 1fr;
    }
    .user-elem{
        display: flex;
        flex-direction: column;
        padding-top: 10px;
    }


</style>