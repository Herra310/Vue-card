<template>
  <div class="product">
    <div :class="'product-inner ' + product.color">
      <div class="product-text-wrap">
        <h2 class="bg-text">
          {{ product.bgtext }}
        </h2>
      </div>
      <div class="product-img-wrap">
        <img :src="product.src" class="imgs" />
      </div>
      <div class="product-detail">
        <h2>{{ product.title }}</h2>
        <p>
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dignissimos
          amet culpa aperiam reiciendis quis veniam hic officia rem id sunt
          asperiores sit dolore modi libero fugit autem recusandae, ducimus
          doloremque!
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "product",
  props: ["product"],
};
</script>

<style>
.product {
  flex: 1 1 33.333%;
  width: 100%;
  padding: 25px;
}

.product-inner {
  position: relative;
  padding: 25px;
  box-shadow: 0 0 16px rgba(0, 0, 0, 0.25);
  perspective: 1100px;
}

.product-inner.green {
  background-image: linear-gradient(to bottom right, #24d484, #116432);
}
.product-inner.blue {
  background-image: linear-gradient(to bottom left, #24d484, #2474c4 70%);
}
.product-inner.pink {
  background-image: linear-gradient(to bottom right, #f444a4, #1168d4);
}

.product-text-wrap {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
  overflow: hidden;
  perspective: 1100px;
}

.product-text-wrap h2 {
  font-size: 120px;
  color: #313131;
  font-weight: 900;
  opacity: 0.2;
  transform-origin: center;
}

.product-img-wrap {
  position: relative;
  z-index: 1;
  transform-origin: center;
}

.product-img-wrap .imgs {
  width: 100%;
  filter: drop-shadow(0px 0px 12px rgba(0, 0, 0, 0.25));
}

.product-detail {
  background: #eee;
  padding: 25px;
  margin: 0px -25px -25px;
}

.product-detail h2 {
  font-size: 24px;
  font-weight: 700px;
  color: #676767;
  margin-bottom: 15px;
}

.product-detail p {
  font-size: 14px;
  line-height: 1.5;
  font-weight: 300;
  color: #676767;
}
</style>
