<template>
    <header class="main-header">
      <nav class="main-nav">
        <ul class="nav-links">
          <nuxt-link to="/blog" tag="li" class="nav-link"><a>All posts</a></nuxt-link>
          <nuxt-link to="/about" tag="li" class="nav-link"><a>About</a></nuxt-link>
        </ul>
      </nav>
    </header>
</template>

<script>
    export default {
        name: 'TheHeader'
    }
</script>

<style scoped>
  .main-header {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    background: #022d30;
    height: 4.5rem;
  }

  .main-nav {
    height: 100%;
  }

  .nav-links {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
  }

  .nav-link {
    height: 100%;
    display: flex;
    justify-items: center;
    align-items: center;
    margin: 0 1rem;
    padding: 0.3rem;
  }

  .nav-link a {
    display: block;
    text-decoration: none;
    color: #ffffff;
  }

  .nav-link.nuxt-link-active {
    border-bottom: 3px solid #06c4d1;
  }

  .nav-link a:hover,
  .nav-link a:active,
  .nav-link.nuxt-link-active a{
    color: #06c4d1;
  }
</style>
