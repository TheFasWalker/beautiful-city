<template>
    <div  :class="[activity ? 'active' : '', 'post']">
        <span class="h2">{{ title }}</span>


    </div>
</template>
<script>
export default{
    props: {
        title: String,
        activity:Boolean
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
        &.active{
            background-color: green;
            color: #FFFFFF;
            font-weight: 600;
        }
    }


</style>