<template>
   <div class="container mx-auto">
        <ul class="mt-4">
            <li class="font-bold text-lg" :class="{'fav' : post.fav}">{{ post.title }}| <button @click="handleClick(post)" class="btn-primary">Delete Post</button> | <button class="btn-primary" @click="$emit('fav', post)">Favorite post</button></li>
        </ul>
   </div>
</template>

<script>
export default{
    name: 'SinglePost',
    props:{
        post:{
            type: Object,
            required: true
        }
    },
    methods:{
        handleClick(post){
           this.$emit('delete', post)
        }
    }
}
</script>
<style scoped>
.fav{
    color: red;
}
</style>