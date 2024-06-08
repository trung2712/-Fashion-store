<template>
  <div class="product">
    <div class="product-image">
      <div class="image">
        <img :src="product.image" alt="">
      </div>
    </div>
    <div class="product-content">
      <h3 class="title">
        <a :href="url" target="_blank">{{ title }}</a>
      </h3>
      <p class="brand">Thương hiệu: No brand</p>
      <p class="quantity" v-if="product.quantity > 0">Còn lại: {{ product.quantity }} Sản phẩm</p>
      <p class="quantity" v-else>Sản phẩm đã hết hàng</p>

      <div class="wrapper-price">
        <div class="final-price">{{ formatFinalPrice }}</div>
        <div class="origin-price">{{ formatOriginalPrice }}</div>
        <div class="sale-price">-{{ sale * 100 }}%</div>
      </div>
      <div class="wrapper-color">
        <div class="text">Màu sắc</div>
        <div class="list-color">
          <p class="color-text">{{ product.textColor }}</p>
          <ul>
            <li
                v-for="(item, index) in productColors"
                :key="index"
                :class="active(index)"
                @click="handleClickColor(index)"
            >
              <img :src="item.image" :alt="item.textColor">
            </li>
          </ul>
        </div>
      </div>
      <button
          @click="handleAddToCart"
          class="add-to-cart">Add to cart</button>
    </div>
  </div>
</template>

<script >
export default {
  props: {
    product: Object,
  },
  data() {
    return {
      title: 'Áo thun nam thể thao hàng VNXK vải dày mịn - Vải Đốm',
      url: 'https://www.lazada.vn/products/ao-thun-nam-the-thao-hang-vnxk-vai-day-min-vai-dom-i265780948-s382816279.html',
      price: 200000,
      sale: 0.2,
      selectedProduct: 2,
    };
  },
  computed :{
    // định dạng giá bản gốc
    formatOriginalPrice() {
      const number = this.price;
      return new Intl.NumberFormat('de-DE', { style: 'currency', currency: 'VND' }).format(number);
    },
    // định dạng Giá cuối cùng
    formatFinalPrice() {
      const number = this.price - this.sale * this.price;
      return new Intl.NumberFormat('de-DE', { style: 'currency', currency: 'VND' }).format(number);
    },
    productColors() {
      return this.product.listProductDetail;
    }
  },
  methods: {
    handleClickColor(index) {
      this.selectedProduct = index;
    },
    active(index) {
      return {
        active: this.selectedProduct === index
      };
    },
    handleAddToCart() {
      if (this.cardNumber + 1 > this.product.quantity) {
        alert('Hiện tại lượng không đủ');
      } else {
        this.cardNumber += 1;
      }
    }
  }
};
</script>

<style scoped>
.product {
  display: flex;
  margin-top: 20px;
}

.product .product-image {
  flex-basis: 40%;
  max-width: 40%;
  padding-right: 30px;
}

.product .product-content {
  flex-basis: 60%;
}
.title {
  margin-top: 0;
}
.add-to-cart {
  border: 1px solid #ffb916;
  background: #ffb916;
  color: #fff;
  display: inline-block;
  padding: 12px 30px;
  margin-top: 30px;
  text-transform: uppercase;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}
.wrapper-price .final-price {
  color: #f57224;
  font-weight: 700;
  font-size: 22px;
  margin-bottom: 5px;
}

.wrapper-price .origin-price,
.wrapper-price .sale-price {
  font-size: 14px;
  color: #999;
  vertical-align: middle;
}

.wrapper-price .sale-price {
  color: #333;
  margin-left: 5px;
  padding: 3px;
  font-size: 10px;
  border-radius: 5px;
  border: 1px solid #f57224;
}

.wrapper-color {
  display: flex;
  margin-top: 15px;
  border-top: 1px solid #eee;
}

.wrapper-color .text {
  width: 100px;
}
</style>
