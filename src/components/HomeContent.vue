<template>
    <div class="content">
      <div class="main-photo">
        <div class="container">
          <div class="photo-top">
            <img src="../img/s11-2.jpg" alt="image" />
          </div>
          <div class="photo-row">
            <div class="image-box">
              <img src="../img/s12.jpg" alt="image" />
              <router-link class="info" :to="{ name: 'productlist' }">
                mens' wateches <i class="arrow right white"></i>
              </router-link>
              <div class="hover-box">
                <router-link class="info" :to="{ name: 'productlist' }">
                  mens' wateches <i class="arrow right white"></i>
                </router-link>
              </div>
            </div>
            <div class="image-box">
              <img src="../img/s01.jpg" alt="image" />
              <router-link class="info" :to="{ name: 'productlist' }">
                new releases <i class="arrow right white"></i>
              </router-link>
              <div class="hover-box">
                <router-link class="info" :to="{ name: 'productlist' }">
                  new releases <i class="arrow right white"></i>
                </router-link>
              </div>
            </div>
            <div class="image-box">
              <img src="../img/s06.jpg" alt="image" />
              <router-link class="info" :to="{ name: 'productlist' }">
                classic watches <i class="arrow right white"></i>
              </router-link>
              <div class="hover-box">
                <router-link class="info" :to="{ name: 'productlist' }">
                  classic watches <i class="arrow right white"></i>
                </router-link>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="trending-products">
        <div class="container">
          <div class="title topic">
            <div class="line"></div>
            <div class="info">
              <h2>TRENDING PRODUCTS</h2>
              <h4>
                Nam interdum, lacus quis tempor iaculis, nunc mauris tincidunt
                metus,
              </h4>
            </div>
            <div class="line"></div>
          </div>
          <div class="product-bar">
            <div
              class="product"
              v-for="(product, index) in webProductList"
              :key="index"
            >
              <router-link class="image-box" :to="{ name: 'productdetail' }">
                <img v-bind:src="product.imagePath" alt="product" />
                <div class="hover-box">
                  <router-link class="info" :to="{ name: 'productdetail' }">
                    ADD TO CART <i class="fas fa-shopping-cart"></i>
                  </router-link>
                </div>
              </router-link>
              <div class="info">
                <h2>{{ product.series }}</h2>
                <h3 class="name">{{ product.seriesName }}</h3>
                <h3>{{ product.color }}</h3>
                <h3>{{ product.price }}</h3>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="photo-bar">
        <div class="container">
          <div class="slide">
            <div class="photo-row">
              <img src="../img/s10.jpg" alt="image" />
            </div>
          </div>
          <div class="info topic">
            <div class="title">Time Discovered Truth.</div>
            <div class="info">
              <h3>MAN ACCESSORIES</h3>
              <h5>
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Repellat quam, recusandae ut libero nisi qui, error natus optio,
                veniam ea voluptatum sapiente repellendus. Quam molestias
                adipisci voluptas enim illum? Ipsa dolore provident iusto sequi
                voluptates quasi numquam quo atque vitae.
              </h5>
            </div>
          </div>
          <div class="circle">. . . . .</div>
        </div>
      </div>
      <div class="best-selling">
        <div class="container">
          <div class="title topic">
            <div class="line"></div>
            <div class="info">
              <h2>BEST-SELLING PRODUCTS</h2>
              <h4>
                Nam interdum, lacus quis tempor iaculis, nunc mauris tincidunt
                metus,
              </h4>
            </div>
            <div class="line"></div>
          </div>
          <div class="product-bar">
            <div
              class="product"
              v-for="(product, index) in webBestSelling"
              :key="index"
            >
              <router-link class="image-box" :to="{ name: 'productdetail' }">
                <img v-bind:src="product.imagePath" alt="product" />
              </router-link>
              <div class="info">
                <h2>{{ product.series }}</h2>
                <h3 class="name">{{ product.seriesName }}</h3>
                <h3>{{ product.color }}</h3>
                <h3>{{ product.price }}</h3>
              </div>
            </div>
          </div>
          <div class="circle">. . . . .</div>
        </div>
      </div>
      <div class="brand-story">
        <div class="container">
          <img src="../img/s13.jpg" alt="image" />
          <div class="title topic">
            <div class="line"></div>
            <div class="info">
              <h2>BRAND STORY</h2>
              <h4>
                Nam interdum, lacus quis tempor iaculis, nunc mauris tincidunt
                metus,
              </h4>
            </div>
            <div class="line"></div>
          </div>
          <div class="article">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequatur
            dicta inventore sit quo aut quaerat veniam ducimus. Dolorem cumque
            eaque itaque, quam perspiciatis harum provident porro aut explicabo
            consectetur! Tempore autem nostrum temporibus eius voluptate tempora
            iusto, vero, officiis asperiores enim vel excepturi cumque officia
            voluptatibus doloremque quos, facilis doloribus?
          </div>
        </div>
      </div>
      <div class="photo-row-bottom">
        <div class="one">
          <img src="../img/s04.jpg" alt="image" />
        </div>
        <div class="two">
          <img class="top" src="../img/s02.jpg" alt="image" />
          <img src="../img/s07.jpg" alt="image" />
        </div>
        <div class="one">
          <img src="../img/s08.jpg" alt="image" />
        </div>
        <div class="two none">
          <img class="top" src="../img/s03.jpg" alt="image" />
          <img src="../img/s09.jpg" alt="image" />
        </div>
      </div>
    </div>
</template>

<script>
import { initializeApp } from "firebase/app";
import { getDatabase, ref, onValue } from "firebase/database";

export default {
  name: "homerun",
  data() {
    return {
      webProductList: [],
      webBestSelling: [],
      ref: null,
    };
  },
  mounted() {
    const firebaseConfig = {
      apiKey: "AIzaSyAbYLUVJYoITGNvgeEJiLWKwlvEZEgsn7M",
      authDomain: "yama-website.firebaseapp.com",
      databaseURL: "https://yama-website-default-rtdb.firebaseio.com",
      projectId: "yama-website",
      storageBucket: "yama-website.appspot.com",
      messagingSenderId: "1094650287749",
      appId: "1:1094650287749:web:b011ea45db8ec625e5bbec",
      measurementId: "G-6TTRYFGB6X",
    };
    const app = initializeApp(firebaseConfig);
    const database = getDatabase(app);
    const starCountRef = ref(database, "/");
    this.ref = starCountRef;
    onValue(starCountRef, (snapshot) => {
      const data = snapshot.val();
      this.webProductList = data.trendingProduct[0];
      this.webBestSelling = data.bestSelling[0];
    });
  },
};
</script>

<style lang="scss" scoped>
$brand-color: #bfb094;
$gray-color: #5b5b5b;
$green-color: #3e5940;

.title {
  &.topic {
    display: flex;
    .line {
      position: relative;
      top: 20px;
      width: 350px;
      border-top: 1px solid $brand-color;
    }

    .info {
      margin: 0 50px;
    }

    h2 {
      font-weight: 100;
      font-size: 18px;
      letter-spacing: 2px;
      color: $brand-color;
    }

    h4 {
      font-weight: 100;
      letter-spacing: 0.5px;
      font-size: 10px;
      margin-top: 10px;
      color: $gray-color;
    }
  }
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.main-photo {
  width: 100%;
  .container {
    display: flex;
    flex-direction: column;
  }
  .photo-top {
    display: flex;
    width: 100%;
    height: 700px;
    margin-top: 60px;
    .image-box {
      position: relative;
      opacity: 0;
    }
    img {
      flex: 1;
      width: 100%;
      object-fit: cover;
    }
  }
  .hover-box {
    a {
      color: white;
    }
    .arrow.right.white {
      border-color: white;
    }
    opacity: 0;
    width: 100%;
    height: 100%;
    position: absolute;
    right: 0;
    bottom: 0;
    top: 0;
    right: 0;
    background-color: rgba($color: $brand-color, $alpha: 0.8);
    transition: 0.5s ease-in;
  }

  .hover-box:hover {
    opacity: 1;
  }
}

.photo-row {
  display: flex;
  .image-box {
    flex: 1 1 0;
    height: 300px;
    position: relative;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .info {
    position: absolute;
    bottom: 10%;
    left: 10%;
    color: white;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 3px;

    text-decoration: none;
  }
}

.trending-products {
  margin-top: 60px;
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .title {
    &.topic {
      display: flex;
      .line {
        position: relative;
        top: 20px;
        width: 350px;
        border-top: 1px solid $brand-color;
      }

      .info {
        margin: 0 50px;
      }

      h2 {
        font-weight: 100;
        font-size: 18px;
        letter-spacing: 2px;
        color: $brand-color;
      }

      h4 {
        font-weight: 100;
        letter-spacing: 0.5px;
        font-size: 10px;
        margin-top: 10px;
        color: $gray-color;
      }
    }
  }
  .product-bar {
    display: flex;
    margin-top: 60px;
    width: 70%;
    justify-content: space-around;
    flex-wrap: wrap;
    .product {
      display: flex;
      flex-direction: column;
      width: 200px;
      padding: 0 50px;
    }
    .image-box {
      flex: 6 1 250px;
      position: relative;
    }
    img {
      width: 100%;
      height: 350px;
      object-fit: contain;
      &.top {
        position: relative;
        bottom: 15px;
      }
    }
    .info {
      flex: 4 1 0;
      h2 {
        font-weight: 100;
        box-sizing: border-box;
        padding-bottom: 5px;
        color: $brand-color;
        border-bottom: 1px solid $brand-color;
      }
      h3 {
        font-weight: 100;
        font-size: 10px;
        margin: 5px 0;
      }
      .name {
        margin-top: 10px;
        color: $brand-color;
      }
    }

    .hover-box {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba($color: white, $alpha: 0.8);
      opacity: 0;
      transition: 0.3s ease-in;
      display: flex;
      align-items: center;

      a {
        line-height: 2;
        font-size: 14px;
        border: 1px solid $brand-color;
        border-radius: 20px;
        display: flex;
        flex-direction: column;
        text-decoration: none;
        color: $brand-color;

        padding-bottom: 5%;
        box-sizing: border-box;
      }

      &:hover {
        opacity: 1;
      }
    }
  }
}

.photo-bar {
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 60px;
  background-color: $green-color;
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 80%;
    img {
      object-fit: cover;
      width: 100%;
    }
  }
  .slide {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }

  .photo-row {
    box-sizing: border-box;
    flex: 1;
    display: flex;
    height: 400px;
  }

  .info.topic {
    margin-top: 60px;
    color: white;
    display: flex;

    .title {
      flex: 1;
      font-size: 65px;
      text-align: left;
    }
    .info {
      text-align: left;
      flex: 1;
      line-height: 1.5;
    }
    h3 {
      font-weight: 100;
    }
    h5 {
      font-size: 10px;
      font-weight: 100;
      margin-top: 10px;
    }
  }
  .circle {
    color: white;
  }
}

.best-selling {
  padding-bottom: 60px;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: $green-color;
  padding-top: 60px;
  margin-bottom: 60px;
  .container {
    width: 70%;
    background-color: white;
    padding: 50px 100px;
    border-radius: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .title {
    &.topic {
      display: flex;
      .line {
        position: relative;
        top: 20px;
        width: 350px;
        border-top: 1px solid $brand-color;
      }

      .info {
        margin: 0 50px;
      }

      h2 {
        font-weight: 100;
        font-size: 18px;
        letter-spacing: 2px;
        color: $brand-color;
      }

      h4 {
        font-weight: 100;
        letter-spacing: 0.5px;
        font-size: 10px;
        margin-top: 10px;
        color: $gray-color;
      }
    }
  }
  .product-bar {
    display: flex;
    margin-top: 60px;
    align-items: center;
    justify-content: space-around;
    .product {
      display: flex;
      flex-direction: column;
      width: 200px;
      padding: 0 20px;
    }
    .image-box {
      flex: 6 1 250px;
    }
    img {
      width: 100%;
      height: 350px;
      object-fit: contain;
      &.top {
        position: relative;
        bottom: 15px;
      }
    }
    .info {
      flex: 4 1 0;
      h2 {
        font-weight: 100;
        box-sizing: border-box;
        padding-bottom: 5px;
        color: $brand-color;
        border-bottom: 1px solid $brand-color;
      }
      h3 {
        font-weight: 100;
        font-size: 10px;
        margin: 5px 0;
      }
      .name {
        margin-top: 10px;
        color: $brand-color;
      }
    }
  }
  .arr {
    height: 25px;
    background-color: $brand-color;
    width: 25px;
    border-radius: 25px;
  }
  .arrow {
    position: relative;
    left: 2px;
    top: 1.5px;
  }
  .arr-right {
    .arrow {
      left: -1.5px;
    }
  }
}

.brand-story {
  margin-bottom: 60px;
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  img {
    width: 70%;
    border-radius: 200px;
  }
  .article {
    width: 50%;
    font-size: 10px;
    margin-top: 30px;
  }
  .title {
    margin-top: 60px;
  }
}

.photo-row-bottom {
  display: flex;
  margin-bottom: 60px;

  img {
    width: 100%;
    object-fit: cover;
    &.top {
      box-sizing: border-box;
      padding-bottom: 15px;
      flex: 1;
      object-fit: cover;
    }
  }
  .one {
    display: flex;
    flex: 2 1 0;
    box-sizing: border-box;
    padding-right: 15px;
  }
  .two {
    box-sizing: border-box;
    padding-right: 15px;
    flex-direction: column;
    display: flex;
    flex: 1 1 0;
    &.none {
      padding-right: 0;
    }
  }
}


//RWD
@media screen and (max-width: 1200px) {
  .product-bar {
    width: 80vw;
  }

  .title.topic {
    .line {
      display: none;
    }
  }

  .main-photo .photo-top {
    height: auto;
  }
}

@media screen and (max-width: 700px) {
  .nav.margin {
    display: none;
  }

  .best-selling {
    display: none;
  }
  .main-photo .photo-top {
    height: auto;
  }

  .photo-row {
    .image-box {
      height: 180px;
    }
  }

  .brand-story {
    .container {
      top: 0;
      padding: 30px 0;
    }
  }

  .photo-row-bottom {
    top: 0;
    padding-bottom: 30px;
  }

  .photo-bar {
    padding-bottom: 30px;
    .info.topic {
      flex-direction: column;
    }
    .title {
      padding-bottom: 2vh;
      font-size: 13vw;
    }
  }
}

</style>