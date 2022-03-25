<template>
  <main id="app" @mousemove="mousemove">
    <section class="products">
      <Product
        v-for="product in products"
        :key="product.color"
        :product="product"
      />
    </section>
  </main>
</template>

<script>
import Product from "./components/Product";
export default {
  name: "App",
  components: {
    Product,
  },
  data() {
    return {
      products: [
        {
          title: "Nike Air Max",
          color: "green",
          bgtext: "NIKE",
          src: require("./assets/green-shoe.png"),
        },
        {
          title: "Nike flex",
          color: "blue",
          bgtext: "AIR",
          src: require("./assets/blue-shoe.png"),
        },
        {
          title: "Nike Roche Runs",
          color: "pink",
          bgtext: "MAX",
          src: require("./assets/pink-shoe.png"),
        },
      ],
    };
  },
  methods: {
    mousemove(e) {
      let mouseX = e.clientX;
      let mouseY = e.clientY;

      let products = document.querySelectorAll(".products .product");

      for (let i = 0; i < products.length; i++) {
        let product = products[i];

        let productimg = product.querySelector(".product-img-wrap");

        let imgX = mouseX - this.coords(productimg).x;
        let imgY = mouseY - this.coords(productimg).y;

        productimg.style.transform = `translateY(-${imgY/35}px) translateX(-${imgX/35}px) 
        translateZ(120px)`;

        let bgtext = product.querySelector('.bg-text');
        let bgX = mouseX - this.coords(bgtext).x;
                let bgY = mouseY - this.coords(bgtext).y;

        bgtext.style.transform = ` translateX(${bgX/25}px) translateY(${bgY/25}px)`;
      }
    },
    coords(el){
      let coords = el.getBoundingClientRect();

      return {
        x: coords.left /2,
        y: coords.top /2,
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: sans-serif;
}

main {
  width: 100vw;
  min-height: 100vh;
  overflow: hidden;

  background-color: #eee;
  display: flex;
  justify-content: center;
  align-items: center;
}

.products {
  display: flex;
  max-width: 1200px;
  padding: 25px;
  margin: 0 auto;
}
</style>
