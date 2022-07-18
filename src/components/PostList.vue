<template>
   <div class="post" v-for="post in posts" :key="post.id">
      <strong class="post-id">{{post.id}}</strong>
      
      <div>
         <h3>Title: {{post.title}}</h3>
         <p>Description: {{post.description}}</p>
      </div>
   </div>
</template>

<script>
   export default {
      props: {
         posts: {
            type: Array,
            required: true
         }
      }
   }
</script>

<style scoped>
   .post {
      display: flex;
      align-items: center;
      margin-top: 20px;
      padding: 20px;
      border: 2px solid red;
   }

   .post-id {
      margin-right: 10px;
      font-size: 20px;
   }
</style>