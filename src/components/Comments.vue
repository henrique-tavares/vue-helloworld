<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <form-todo v-on:add-todo="addComment" />
    <div class="list-group">
      <div
        class="list-group-item"
        v-for="(comment, idx) in computedComments"
        v-bind:key="idx"
      >
        <span class="comment__author"
          >Autor: <strong>{{ comment.author }}</strong>
        </span>
        <p>{{ comment.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(idx)"
            >Excluir</a
          >
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormTodo from "./FormTodo.vue";

export default {
  name: "Comments",
  components: {
    FormTodo,
  },
  data() {
    return {
      comments: [],
    };
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },
    removeComment(idx) {
      this.comments.splice(idx, 1);
    },
  },
  computed: {
    computedComments() {
      return this.comments.map((comment) => ({
        ...comment,
        author: comment.author.trim() === "" ? "Anônimo" : comment.author,
      }));
    },
  },
  watch: {
    comments(val) {
      console.log(val);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
