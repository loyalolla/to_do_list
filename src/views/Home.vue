<template>
  <div>
    <h2>Home page</h2>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cum dignissimos
      eveniet excepturi expedita impedit numquam quae quas tenetur velit
      voluptas!
    </p>

    <router-link class="bubbly" to="/todos">Todos</router-link>
  </div>
</template>

<style scoped>
.bubbly {
  padding: 0.5rem 2rem;
  border-color: rgba(71, 126, 232, 0.7);
  color: #e1e8ee;
  border-radius: 50px;
  text-decoration: none;
  box-shadow: 0 0 40px 40px rgba(71, 126, 232, 0.7) inset,
    0 0 0 0 rgba(71, 126, 232, 0.7);
  -webkit-transition: all 150ms ease-in-out;
  transition: all 150ms ease-in-out;
  font-size: 1.1rem;
}
.bubbly:hover {
  box-shadow: 0 0 10px 0 rgba(71, 126, 232, 0.7) inset,
    0 0 10px 4px rgba(71, 126, 232, 0.7);
}
</style>
