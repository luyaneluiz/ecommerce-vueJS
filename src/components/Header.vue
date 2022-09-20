<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" />
    <nav v-show="!isMobile">
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/categories">Categories</RouterLink>
      <RouterLink to="/contact">Contact Us</RouterLink>
    </nav>
    <nav>
      <div class="search">
        <img src="./icons/search.svg" alt="" />
      </div>
      <nav v-show="!isMobile">
        <RouterLink to="/favorites">
          <img src="../assets/favorite.svg" alt="" />
        </RouterLink>
        <RouterLink to="/cart">
          <img src="../assets/cart.svg" alt="" />
        </RouterLink>
      </nav>
    </nav>
  </header>
</template>

<style scoped>
header {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 calc(30px + 5%);
}

.logo {
  width: max(3vw, 50px);
  height: max(3vw, 50px);
}

nav {
  display: flex;
  align-items: center;
}

nav a,
.search {
  padding: 0 1rem;
  display: flex;
  align-items: center;
}

nav a.router-link-exact-active {
  color: rgb(23, 174, 124);
  font-weight: bold;
}

a,
.green {
  color: hsla(161, 100%, 9%, 0.921);
}

a:hover {
  color: rgb(41, 177, 132);
}
</style>

<script>
export default {
  name: "Header",
  data() {
    return {
      windowWidth: window.innerWidth,
    };
  },
  mounted() {
    window.onresize = () => {
      this.windowWidth = window.innerWidth;
    };
  },
  computed: {
    isMobile() {
      return this.windowWidth < 632;
    },
  },
};
</script>
