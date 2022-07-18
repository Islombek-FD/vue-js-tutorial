<template>
   <form @submit.prevent>
      <h2>Create post</h2>
      
      <input @input="post.title = $event.target.value" v-bind:value="post.title" class="input" type="text" placeholder="Write title">
      <input @input="post.description = $event.target.value" v-bind:value="post.description" class="input" type="text" placeholder="Write description">
      <button @click="createPost" class="btn">Add post</button>
   </form>
</template>

<script>
   export default {
      data() {
         return {
            post: {
               title: '',
               description: ''
            }
         }
      },
      methods: {
         createPost() {
            this.post.id = Date.now();
            this.$emit('create', this.post);
            this.post = {
               title: '',
               description: ''
            }
         }
      }
   }
</script>

<style scoped>
   .input {
      display: block;
      width: 100%;
      margin-bottom: 10px;
      padding: 10px;
      border: 2px solid gray;
   }

   .input:focus {
      outline: none;
   }

   .btn {
      width: 100%;
      padding: 10px;
      background-color: rgb(71, 71, 240);
      color: white;
      border: none;
      cursor: pointer;
   }
</style>