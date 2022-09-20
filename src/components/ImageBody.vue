<template>
  <div class="image__body">
    <img
      src="https://images.unsplash.com/photo-1611849362103-5c99622adf18?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8NDF8fHByb2R1Y3R8ZW58MHwwfDB8fA%3D%3D&auto=format&fit=crop&w=400&q=60"
      alt=""
    />
  </div>
</template>

<style>
.image__body {
  display: flex;
  justify-content: center;
}

.image__body img {
  margin: 40px 0;
  width: 75vw;
  border-radius: 25px;
  height: 25vh;
  object-fit: cover;
  object-position: center;
}
</style>

<script>
export default {
  name: "ImageBody",
};
</script>
