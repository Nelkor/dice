<template>
  <div class="header">
    <div class="inner">
      <router-link
        class="header-link"
        to="/"
      >Главная</router-link>

      <router-link
        class="header-link"
        to="/about"
      >О нас</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style lang="scss" scoped>
  .header {
    width: 100%;
    height: 96px;
    background: #fff;
    margin-bottom: 16px;
    display: flex;
    justify-content: center;
    box-shadow: 0 2px 2px rgba(0, 0, 0, .05);
  }

  .inner {
    width: 1000px;
    box-sizing: border-box;
    padding: 0 24px;
    display: flex;
    align-items: center;
  }

  .header-link {
    color: inherit;
    text-decoration: none;
    font-weight: 600;
    margin: 0 24px;

    &:hover {
      color: crimson;
    }
  }
</style>
