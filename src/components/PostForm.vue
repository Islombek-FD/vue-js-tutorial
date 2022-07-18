<template>
   <form @submit.prevent>
      <h2>Create post</h2>
      
      <input @input="post.title = $event.target.value" v-bind:value="post.title" class="input" type="text" placeholder="Write title">
      <input @input="post.description = $event.target.value" v-bind:value="post.description" class="input" type="text" placeholder="Write description">
      <my-button @click="createPost" class="btn btn-primary block">Add post</my-button>
   </form>
</template>

<script>
   import MyButton from '@/components/UI/MyButton.vue';
   export default {
      components: {
         MyButton
      },
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
</style>