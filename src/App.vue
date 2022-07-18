// v-bind:posts = :post;
// v-on:click = @click;

<template>
   <div class="container">
      <h1>Create post</h1>

      <my-button @click="createPostModal" class="btn btn-primary">Add post</my-button>

      <my-modal v-model:show="showModal">
         <post-from @create="createPost" />
      </my-modal>

      <post-list @remove="removePost" :posts="posts" />
   </div>
</template>

<script>
   import PostFrom from './components/PostForm.vue';
   import PostList from '@/components/PostList.vue';
import MyButton from './components/UI/MyButton.vue';

   export default {
      components: {
         PostFrom,
         PostList,
            MyButton,
      },
      data() {
         return {
            posts: [
               { id: 1, title: 'React Js', body: 'React Js darslari' },
               { id: 2, title: 'Angular Js', body: 'Angular Js darslari' },
               { id: 3, title: 'Vue Js', body: 'Vue Js darslari' },
            ],
            showModal: false 
         }
      },
      methods: {
         createPostModal() {
            this.showModal = true;
         },
         createPost(post) {
            this.posts.push(post);
            this.showModal = false;
         },
         removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id);
         }
      }
   }
</script>


<style>
   * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
   }

   .container {
      max-width: 500px;
      margin: 0 auto;
   }
</style>