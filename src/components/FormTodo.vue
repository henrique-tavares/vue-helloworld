<template>
  <div class="form-todo form-group">
    <p>
      <input
        type="text"
        class="form-control"
        placeholder="Nome"
        name="Author"
        v-model="author"
      />
    </p>

    <p>
      <textarea
        name="message"
        placeholder="Comentário"
        class="form-control"
        v-model="message"
      ></textarea>
    </p>

    <button type="submit" class="btn btn-primary" v-on:click="addComment">
      Comentar
    </button>
  </div>
</template>

<script>
export default {
  name: "FormTodo",
  data() {
    return {
      author: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      if (this.message.trim() === "") {
        return;
      }

      this.$emit("add-todo", {
        author: this.author,
        message: this.message,
      });

      this.author = "";
      this.message = "";
    },
  },
};
</script>