<template>
  <form @submit.prevent="onSubmit">
    <input
      type="text"
      placeholder="What Do You Want to Do..."
      v-model="title"
    />
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };

        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
input {
  width: 400px;
  margin-bottom: 1rem;
  margin: 0.5rem;
  height: 50px;
  border-radius: 25px;
  border-color: rgba(71, 126, 232, 0.7);
}
button {
  padding: 0.5rem 2rem;
  border-color: rgba(71, 126, 232, 0.7);
  color: #e1e8ee;
  border-radius: 50px;
  text-decoration: none;
  box-shadow: 0 0 40px 40px rgba(71, 126, 232, 0.7) inset,
    0 0 0 0 rgba(71, 126, 232, 0.7);
  transition: all 150ms ease-in-out;
  font-size: 1.1rem;
}
.button:hover {
  box-shadow: 0 0 10px 0 rgba(71, 126, 232, 0.7) inset,
    0 0 10px 4px rgba(71, 126, 232, 0.7);
}
</style>
