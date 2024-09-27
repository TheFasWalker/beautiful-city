<template>
    <div class="post">
        <h2 class="h2">{{ title }}</h2>
        <div class="description">
            <span>post description</span>
            <p>{{ description }}</p>
            <button class="post-button" :data-id="id" >showComments</button>
        </div>
        
    </div>
</template>
<script>
export default{
    props: {
        title:String,
        description:String,
        id:Number
    }
}
</script>
<style lang="scss" scoped>
    .post{
        border: 2px solid rgb(153, 146, 146);
        border-radius: 10px;
        padding: 10px 20px;
    }
    .description{
        padding-top: 20px;
    }
    .post-button{
        margin-top: 20px;
        cursor: pointer;
    }
    
</style>