<template>
  <main>
    <div class="product__container">
      <div class="product__image">
        <img :src="image" :alt="title" />
      </div>

      <aside>
        <h2>{{ title }}</h2>
        <div class="product__stars">
          <img
            class="star__check"
            src="../components/icons/star_check.svg"
            alt="Estrela preenchida"
          />
          <img src="../components/icons/star.svg" alt="Estrela vazada" />
          <img src="../components/icons/star.svg" alt="Estrela vazada" />
          <img src="../components/icons/star.svg" alt="Estrela vazada" />
          <img src="../components/icons/star.svg" alt="Estrela vazada" />
        </div>
        <div class="product__share"></div>
        <h3>{{ price }}</h3>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa ipsum
          quo eveniet? Cupiditate sit quo ab quisquam id illum. Consequuntur
          quisquam id, tempore quasi illo tenetur illum inventore ea! Incidunt!
        </p>
        <div class="product__amount">
          <p>Quantidade</p>
          <div class="amount__counter">
            <button class="counter__remove">-</button>
            <input type="text" />
            <button class="counter__add"></button>
          </div>
          <div class="product__actions">
            <button class="action__cart"></button>
            <button class="action__favorite"></button>
          </div>
        </div>
      </aside>
    </div>
  </main>
</template>

<style>
.product__container {
  display: flex;
}

.product__image {
  width: 400px;
  height: 400px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

<script>
import axios from "axios";

export default {
  data() {
    return {
      id: this.$route.params.id,
      image: "",
      title: "",
      price: "",
    };
  },
  created() {
    axios.get("http://127.0.0.1:5174/products.json").then((res) => {
      const product = res.data.products.filter((element) => {
        return this.id == element.id;
      });

      this.image = product[0].image;
      this.title = product[0].title;
      this.price = product[0].price;
    });
  },
};
</script>
