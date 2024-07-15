<template>
  <div class="app">
    <Sidebar />
    <RouterView />
  </div>
</template>

<script setup>
import Sidebar from "./components/Sidebar.vue";
</script>

<style lang="scss">
:root {
  --yellow: #fcb901;
  --dark: #57022f;
  --dark-alt: #642443;
  --light: #f1f5f9;
  --sidebar-width: 220px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}

body {
  background-color: var(--light);
}

button {
  cursor: pointer;
  appearance: none;
  border: none;
  outline: none;
  background: none;
}

.app {
  display: flex;
  main {
    flex: 1 1 0;
    padding: 2rem;
    @media (max-width: 768px) {
      padding-left: 6rem;
    }
    h1 {
      font-size: 30px;
      font-weight: 600;
    }
    p {
      font-size: 20px;
      font-weight: 500;
    }
  }
}

</style>
