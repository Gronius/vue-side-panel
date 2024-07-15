<template>
  <aside :class="{ 'is-expanded': expanded }">
    <div class="logo">
      <img src="../assets/dog.png" alt="Logo" />
    </div>

    <div class="menu-toggle-wrap">
      <button class="menu-toggle" @click="toggleMenu">
        <span class="material-icons">double_arrow</span>
      </button>
    </div>

    <h3>Menu</h3>
    <div class="menu">
      <RouterLink class="button" to="/">
        <span class="text">Home</span>
      </RouterLink>
      <RouterLink class="button" to="/about">
        <span class="text">About</span>
      </RouterLink>
      <RouterLink class="button" to="/blog">
        <span class="text">Blog</span>
      </RouterLink>
      <RouterLink class="button" to="/contact">
        <span class="text">Contact</span>
      </RouterLink>
    </div>

    <div class="flex"></div>

    <div class="menu">
      <RouterLink class="button" to="/networks">
        <span class="text">Networks</span>
      </RouterLink>
    </div>
  </aside>
</template>

<script setup>
import { ref } from "vue";

const expanded = ref(localStorage.getItem("expanded") === "true");

const toggleMenu = () => {
  expanded.value = !expanded.value;
  localStorage.setItem("expanded", expanded.value);
};
</script>

<style lang="scss" scoped>
aside {
  display: flex;
  flex-direction: column;
  background-color: var(--dark);
  backdrop-filter: 5px;
  color: var(--light);
  width: calc(2rem + 32px);
  min-height: 100vh;
  overflow: hidden;
  padding: 1rem;
  transition: 0.2s ease-out;

  .flex {
    flex: 1;
  }

  .logo {
    margin-bottom: 1rem;

    img {
      width: 3rem;
    }
  }

  .menu-toggle-wrap {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 1rem;
    position: relative;
    top: 0;
    transition: 0.2s ease-out;

    .menu-toggle {
      transition: 0.2s ease-out;

      .material-icons {
        font-size: 2rem;
        color: var(--light);
        transition: 0.2s ease-out;
      }

      &:hover {
        .material-icons {
          color: var(--yellow);
          transform: translateX(0.2rem);
        }
      }
    }
  }

  h3,
  .button .text {
    opacity: 0;
    transition: 0.3s ease-out;
  }

  h3 {
    color: var(--yellow);
    font-size: 1.2rem;
    margin-bottom: 2rem;
    text-transform: uppercase;
  }

  .menu {
    margin: 0 -1rem;

    .button {
      display: flex;
      align-items: center;
      text-decoration: none;
      padding: 0.5rem 1rem;
      transition: 0.2s ease-out;

      .text {
        font-size: 1.3rem;
        color: var(--light);
        transition: 0.2s ease-out;
      }

      &:hover,
      &.router-link-exact-active {
        background-color: var(--dark-alt);

        .material-icons,
        .text {
          color: var(--yellow);
        }
      }

      &.router-link-exact-active {
        border-right: 5px solid var(--yellow);
      }
    }
  }

  &.is-expanded {
    width: var(--sidebar-width);
    .menu-toggle-wrap {
      top: -3.4rem;
      .menu-toggle {
        transform: rotate(-180deg);
      }
    }

    h3,
    .button .text {
      opacity: 1;
    }

  }

  @media (max-width: 768px) {
    position: fixed;
    z-index: 100;
  }
}
</style>