<template>
  <main>
    <section class="header">
      <div class="header__image"></div>
    </section>
    <div class="categories">
      <nav class="categories__list">
        <a
          v-for="category in categories"
          :key="category.name"
          :class="{ active: currentCategory === category.id }"
          @click="currentCategory = category.id"
        >
          {{ category.name }}
        </a>
      </nav>
      <component
        :is="categories[currentCategory].component"
        class="category"
      ></component>
    </div>
  </main>
</template>

<style>
main {
  padding: min(5%, 30px) 30px;
}
section.header {
  display: flex;
  justify-content: center;
  height: 33vw;
}

.header__image {
  width: 90%;
  height: 100%;

  background: url(https://images.unsplash.com/photo-1558769132-cb1aea458c5e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8Mnx8Y2xvdGhlc3xlbnwwfHwwfHw%3D&auto=format&fit=crop&w=400&q=60);
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;

  border-radius: 15px;
}

.categories {
  width: 100%;
  margin: 40px 0 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.categories__list {
  display: flex;
  justify-content: space-around;
  width: max(70%, 315px);
  padding: 20px;
}

.categories__list a {
  color: var(--text-ligth);
}

.categories__list a:hover,
.categories__list a.router-link-exact-active,
a.active {
  color: var(--text-color-brown);
  font-weight: bold;
}

.products a {
  color: black;
}
</style>

<script>
import ElectronicsView from "../components/Categories/ElectronicsView.vue";
import ShoesView from "../components/Categories/ShoesView.vue";
import ShirtsView from "../components/Categories/ShirtsView.vue";
import PantsView from "../components/Categories/PantsView.vue";

export default {
  data() {
    return {
      categories: [
        {
          id: 0,
          name: "Electronics",
          component: ElectronicsView,
        },
        {
          id: 1,
          name: "Shoes",
          component: ShoesView,
        },
        {
          id: 2,
          name: "Shirts",
          component: ShirtsView,
        },
        {
          id: 3,
          name: "Pants",
          component: PantsView,
        },
      ],
      currentCategory: 0,
    };
  },
};
</script>
