<template>
    <div class="comment">
        <div class="header">
            <span class="username"> {{ username }}</span>
            <button :data-userid='email'>UserData</button>
        </div>

        <p>{{ body }}</p>
    </div>
</template>
<script>
export default {
    props: {
        username: String,
        body: String.appl,
        email:String
    }
}
</script>
<style lang="scss" scoped>
    .comment{
        border: 2px solid rgb(34, 185, 34);
        border-radius: 10px;
        padding: 20px 30px;
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

</style>