<template>
   <div class="container">
      <post-from @create="createPost" />
      <post-list @remove="removePost" :posts="posts" />
   </div>
</template>

// v-bind:posts = :post;
// v-on:click = @click;

<script>
   import PostFrom from './components/PostForm.vue';
   import PostList from '@/components/PostList.vue';

   export default {
      components: {
         PostFrom,
         PostList
      },
      data() {
         return {
            posts: [
               { id: 1, title: 'React Js', description: 'React Js darslari' },
               { id: 2, title: 'Angular Js', description: 'Angular Js darslari' },
               { id: 3, title: 'Vue Js', description: 'Vue Js darslari' },
            ],
            title: '',
            description: ''
         }
      },
      methods: {
         createPost(post) {
            this.posts.push(post)
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