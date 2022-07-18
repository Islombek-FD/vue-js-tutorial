<template>
   <div>
      <h2>Pragraming languages list</h2>

      <post-item @remove="$emit('remove', post)" v-for="post in posts" :key="post.id" :post='post'/>
   </div>
</template>

<script>
   import PostItem from '@/components/PostItem.vue';

   export default {
      components: {
         PostItem
      },
      props: {
         posts: {
            type: Array,
            required: true
         },
      },
   }
</script>

<style scoped>
   
</style>