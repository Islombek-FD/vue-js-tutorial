<template>
   <form @submit.prevent>
      <h2>Create post</h2>
      
      <my-input 
         v-model="post.title"
         class="input" 
         type="text" 
         placeholder="Write title"
      />
         
      <my-input
         v-model="post.description"
         class="input" 
         type="text" 
         placeholder="Write description"
      />

      <my-button @click="createPost" class="btn btn-primary block">Add post</my-button>
   </form>
</template>

// @input="post.title = $event.target.value" v-bind:value="post.title" = v-model='post.title'
// @input="post.description = $event.target.value" v-bind:value="post.description" = v-model='post.description'

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
   
</style>