<template>
  <main class="products">
    <div class="products__item" v-for="product in products" :key="product">
      <router-link :to="{ name: 'product', params: { id: product.id } }">
        <img class="item__image" :src="product.image" alt="" />
      </router-link>
      <section>
        <router-link
          :to="{ name: 'product', params: { id: product.id } }"
          style="width: 90%"
        >
          <h2>{{ product.title }}</h2>
          <h1>{{ product.price }}</h1>
        </router-link>
        <div class="item__actions">
          <img
            v-on:click="addFavorite(product)"
            v-if="!inFavorite(product)"
            src="../../assets/favorite-inactive.svg"
            alt=""
          />
          <img
            v-on:click="removeFavorite(product)"
            v-if="inFavorite(product)"
            src="../../assets/favorite.svg"
            alt=""
          />
        </div>
      </section>
    </div>
  </main>
</template>

<style scoped>
.products {
  display: flex;
  gap: 4vw;
  justify-content: center;
  flex-wrap: wrap;
}

.products__item {
  height: min(100vh, 450px);
  width: min(75vw, 315px);
  border-radius: 15px;
  overflow: hidden;
  background-color: rgb(249 249 249);
}

.item__image {
  width: 100%;
  height: 75%;
  object-position: center;
  object-fit: cover;
}

section {
  width: 100%;
  height: 25%;
  display: flex;
  align-items: center;
  padding: 15px;
}

.products__item h2 {
  font-size: 1.1em;
}

.products__item h1 {
  font-size: 1.3em;
  font-weight: bold;
}

.item__actions {
  display: flex;
  gap: 8px;
}
.item__actions img {
  width: 33px;
}
</style>

<script>
import axios from "axios";

export default {
  data() {
    return {
      products: [
        {
          id: 1,
          image:
            "https://images.unsplash.com/photo-1544117519-31a4b719223d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE1fHx8ZW58MHx8fHw%3D&auto=format&fit=crop&w=400&q=60",
          title: "SmartWatch Apple",
          price: "$ 300.00",
        },
        {
          id: 2,
          image:
            "https://images.unsplash.com/photo-1583394838336-acd977736f90?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8OXx8cHJvZHVjdHxlbnwwfDF8MHx8&auto=format&fit=crop&w=400&q=60",
          title: "HeadPhone Xiaomi",
          price: "$ 100.00",
        },
        {
          id: 3,
          image:
            "https://images.unsplash.com/photo-1564466809058-bf4114d55352?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTF8fHByb2R1Y3R8ZW58MHwxfDB8fA%3D%3D&auto=format&fit=crop&w=400&q=60",
          title: "Camera Nikon",
          price: "$ 100.00",
        },
        {
          id: 4,
          image:
            "https://images.unsplash.com/photo-1600080972464-8e5f35f63d08?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTZ8fHByb2R1Y3R8ZW58MHwxfDB8fA%3D%3D&auto=format&fit=crop&w=400&q=60",
          title: "Camera Nikon",
          price: "$ 100.00",
        },
        {
          id: 5,
          image:
            "https://images.unsplash.com/photo-1555375771-14b2a63968a9?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MzV8fHByb2R1Y3R8ZW58MHwxfDB8fA%3D%3D&auto=format&fit=crop&w=400&q=60",
          title: "iPhone XR",
          price: "$ 100.00",
        },
        {
          id: 6,
          image:
            "https://images.unsplash.com/photo-1516962126636-27ad087061cc?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8ODh8fHByb2R1Y3R8ZW58MHwxfDB8fA%3D%3D&auto=format&fit=crop&w=400&q=60",
          title: "Camera Polaroid",
          price: "$ 100.00",
        },
      ],

      favorite: [],
    };
  },
  methods: {
    addFavorite(product) {
      this.favorite.push(product);
      localStorage.setItem("favorite", JSON.stringify(this.favorite));
    },

    inFavorite(product) {
      if (localStorage.getItem("favorite")) {
        this.favorite = JSON.parse(localStorage.getItem("favorite"));
      }
      return this.favorite.find((element) => element["id"] == product.id)
        ? true
        : false;
    },

    removeFavorite(product) {
      if (this.inFavorite(product)) {
        this.favorite = this.favorite.filter((prod) => product.id !== prod.id);
        localStorage.setItem("favorite", JSON.stringify(this.favorite));
      }
    },
  },

  created() {
    axios.get("http://127.0.0.1:5173/products.json").then((res) => {
      this.products = res.data.products.filter((element) => {
        return element.category === "Electronics";
      });
    });
  },
};
</script>
