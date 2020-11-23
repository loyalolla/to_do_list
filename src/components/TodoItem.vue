<template>
  <li>
    <span v-bind:class="{ done: todo.completed }">
      <input
        type="checkbox"
        class="checkbox"
        v-on:change="todo.completed = !todo.completed"
      />
      <strong>{{ index + 1 }}</strong>
      {{ todo.title | uppercase }}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
  height: 50px;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
  background: rgba(71, 126, 232, 0.7);
  border: 5px solid transparent;
  border-radius: 20px;
  color: #f2f6f9;
  font-weight: bold;
  font-size: 1.1rem;
  box-shadow: 0px 10px 25px 0px rgba(165, 219, 207, 0.35);
  transition: all 0.25s ease;
}

.rm {
  border-color: rgba(97 128 186);
  color: #fff;
  border-radius: 50px;
  height: 25px;
  box-shadow: 0 0 40px 40px rgba(97 128 186) inset, 0 0 0 0 rgba(97 128 186);
  -webkit-transition: all 150ms ease-in-out;
  transition: all 150ms ease-in-out;
  font-size: 1.1rem;
}

input {
  margin-right: 1rem;
}
.checkbox {
  content: "";
  width: 50px;
  height: 26px;
}

.done {
  text-decoration: line-through;
}
</style>
