<template>
  <main>
    <h2 class="favorites__title">Minha lista de desejos</h2>
    <template v-if="isEmpty">
      <section class="favorites__list-empty">
        <h3 class="favorites__subtitle">Sua lista está vazia</h3>
        <img
          class="favorites__heart"
          src="../assets/undraw_favorites-empty.svg"
          alt=""
        />
        <p class="favorites__text">
          Adicione seus favoritos à sua lista de desejos!
        </p>
        <router-link to="/">
          <button>Ir as compras</button>
        </router-link>
      </section>
    </template>
    <template v-else>
      <section class="favorites__list">
        <div v-for="product in favorites" :key="product">
          <img class="item__image" :src="product.image" alt="" />
          <h2>{{ product.title }}</h2>
          <h1>{{ product.price }}</h1>
        </div>
      </section>
    </template>
  </main>
</template>

<style>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: calc(100% - 100px);
}

.favorites__title {
  font-weight: bold;
}

.favorites__list-empty {
  display: flex;
  gap: 3vh;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  padding: 10% 0 30% 0;
}

.favorites__subtitle {
  font-size: max(2.8vh, 24px);
}

.favorites__heart {
  width: max(200px, 40%);
  height: max(200px, 40%);
}

.favorites__text {
  font-size: max(2vh, 20px);
  text-align: center;
}

button {
  cursor: pointer;
  padding: 15px 25px;

  font-size: max(1vh, 16px);
  font-weight: bold;

  color: #fff;
  background-color: rgb(23, 174, 124);
  border: none;
  border-radius: 5px;
}
</style>

<script>
export default {
  data() {
    return {
      favoritesEmpty: true,
      favorite: [],
    };
  },
  computed: {
    isEmpty() {
      return (this.favoritesEmpty =
        JSON.parse(localStorage.favorite).length === 0);
    },
    favorites: function () {
      return (this.favorite = JSON.parse(localStorage.getItem("favorite")));
    },
  },
};
</script>
