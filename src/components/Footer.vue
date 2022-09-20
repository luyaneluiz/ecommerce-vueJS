<template>
  <footer>
    <div class="footer__mobile" v-show="isMobile">
      <img src="../assets/home.svg" alt="" />
      <img src="../assets/favorite-inactive.svg" alt="" />
      <img src="../assets/cart.svg" alt="" />
      <img src="../assets/user.svg" alt="" />
    </div>
    <div class="footer__desktop" v-show="!isMobile">
      <div class="footer__aside">
        <img src="@/assets/logo.svg" alt="" width="40px" />
        <div class="aside__icons">
          <img src="../assets/facebook.svg" alt="" />
          <img src="../assets/twitter.svg" alt="" />
          <img src="../assets/instagram.svg" alt="" />
        </div>
        <p>Vue E-commerce</p>
      </div>

      <div class="footer__aside">
        <h2>Map</h2>
        <ul>
          <li>Home</li>
          <li>Categories</li>
          <li>Cart</li>
          <li>Serch</li>
          <li>Favorites</li>
        </ul>
      </div>

      <div class="footer__aside">
        <h2>Links</h2>
        <ul>
          <li>Electronics</li>
          <li>Shoes</li>
          <li>Shirts</li>
          <li>Pants</li>
        </ul>
      </div>

      <div class="footer__aside">
        <h2>Contact</h2>
        <ul>
          <li>+55 48 9876 5432</li>
          <li>ecommerce@vue.com.br</li>
          <li>R. Lameira de Almeida - Criciúma/SC</li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<style>
footer {
  height: 75px;
}
.footer__mobile {
  position: fixed;
  background-color: #8ec0b0;
  border-radius: 25px 25px 0 0;
  bottom: 0;
  height: 75px;
  width: 100vw;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.footer__mobile img {
  filter: invert(1);
  width: 30px;
  height: 30px;
}

.footer__desktop {
  display: flex;
  justify-content: space-around;

  padding: 50px;

  background-color: rgb(56, 51, 51);
  color: white;
}

.footer__desktop h2 {
  font-weight: bold;
}

.aside__icons img {
  filter: invert(1);
  margin: 10px 5px;
}

.footer__aside ul {
  list-style: none;
  padding: 0;
}

.footer__aside li {
  padding: 5px 0;
  cursor: pointer;
}
</style>

<script>
export default {
  name: "Footer",
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
