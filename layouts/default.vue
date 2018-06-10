<template>
  <div>
    <TheHeader></TheHeader>
    <main class="main-content">
      <nuxt/>
    </main>
  </div>
</template>

<style>
  *, *:before, *:after
  {
    box-sizing: border-box;
  }

  body {
    font-family: 'Lato', sans-serif;
    margin: 0;
  }

  .main-content {
    margin-top: 4.5rem;
  }
</style>
<script>
  import TheHeader from "@/components/TheHeader/TheHeader";
  export default {
    components: {
      TheHeader
    }
  }
</script>
