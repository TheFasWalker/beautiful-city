<template>
    <div class="post" :data-id="id">
        <span class="h2">{{ title }}</span>


    </div>
</template>
<script>
export default{
    props: {
        title:String,
    }
}
</script>
<style lang="scss" scoped>
    .post{
        border: 2px solid rgb(153, 146, 146);
        border-radius: 10px;
        padding: 10px 20px;
        cursor: pointer;
        &:hover{
            background: gray;
            box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
            color: #FFFFFF;
        }
    }


</style>