<template>
  <main>
    <div class="product__container">
      <aside class="product__image">
        <img :src="image" :alt="title" />
      </aside>

      <aside>
        <h2>{{ title }}</h2>

        <div class="product__stars">
          <img
            src="../components/icons/star_check.svg"
            alt="Estrela preenchida"
          />
          <img
            src="../components/icons/star_check.svg"
            alt="Estrela preenchida"
          />
          <img
            src="../components/icons/star_check.svg"
            alt="Estrela preenchida"
          />
          <img
            src="../components/icons/star_check.svg"
            alt="Estrela preenchida"
          />
          <img src="../components/icons/star.svg" alt="Estrela vazada" />
        </div>

        <div class="product__share"></div>

        <h3 class="product__price">{{ price }}</h3>

        <div class="product__description">
          <h4>Description</h4>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa ipsum
            quo eveniet? Cupiditate sit quo ab quisquam id illum. Consequuntur
            quisquam id, tempore quasi illo tenetur illum inventore ea!
            Incidunt!
          </p>
        </div>

        <div class="product__amount">
          <h4>Quantidade</h4>
          <div class="amount__counter">
            <button class="counter__remove">-</button>
            <input class="counter__view" type="text" />
            <button class="counter__add">+</button>
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
main {
  display: flex;
  justify-content: center;
}

.product__container {
  display: flex;
  gap: 20px;
  width: min(80vw, 1200px);
}

aside {
  width: 50%;
}

.product__image {
  height: 400px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

.product__stars img {
  width: 32px;
  height: 32px;
}

.product__price {
  font-size: 32px;
  font-weight: bold;
}

.product__description h4,
.product__amount h4 {
  font-weight: bold;
  margin-top: 20px;
}

.amount__counter {
  width: 120px;
  height: 30px;
  display: grid;
  grid-template-columns: 30% 40% 30%;
}

.amount__counter button,
.amount__counter input {
  border: 1px solid #cacaca;
  background-color: #fff;
}

.amount__counter button:hover,
.amount__counter input:hover {
  border: 1px solid #a1a1a1;
}

.counter__remove {
  border-radius: 50% 0 0 50%;
}

.counter__add {
  border-radius: 0 50% 50% 0;
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
    axios.get("http://127.0.0.1:5173/products.json").then((res) => {
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
