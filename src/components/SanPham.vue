<template>
  <div class="product">
    <div class="product-image">
      <div class="image">
        <img :src="selectedProduct.image" alt="">
      </div>
    </div>
    <div class="product-content">
      <div class="product-details">
      <h3 class="title">
        <a >Áo thun nam thể thao hàng VNXK vải dày mịn - Vải Đốm</a>
      </h3>
        <p class="brand">Thương hiệu: Livan Sport.</p>
        <p class="quantity" v-if="selectedProduct.quantity > 0">Còn lại: {{ selectedProduct.quantity }} Sản phẩm</p>
        <p class="quantity" v-else>Sản phẩm đã hết hàng</p>
      </div>

      <div class="wrapper-price">
        <div class="final-price">{{ giaCuoiCung }}</div>
        <div class="origin-price">{{ giaBanGoc }}</div>
        <div class="sale-price"> -{{ salesHienThi * 100 }}% Giảm </div>
      </div>
      <div class="wrapper-color">
        <div class="text">Màu sắc</div>
        <div class="list-color">
          <p class="color-text">{{ selectedProduct.textColor }}</p>
          <ul>
            <li
                v-for="(item, index) in listProduct"
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

<script>
export default {
  props: {
    listProduct: Array,
    sanPhamDaChon: {
      type: Number,
      default: 0,
    },
    sale: Number,
    price: Number,
  },
  data() {
    return {
      selectedProduct: this.listProduct[this.sanPhamDaChon],
      salesHienThi : 0.2
    };
  },
  computed: {
    giaBanGoc() {
      const number = this.price;
      return new Intl.NumberFormat('de-DE', { style: 'currency', currency: 'VND' }).format(number);
    },
    giaCuoiCung() {
      const finalPrice = this.price - this.sale * this.price;
      return new Intl.NumberFormat('de-DE', { style: 'currency', currency: 'VND' }).format(finalPrice);
    }

  },
  methods: {
    handleClickColor(index) {
      this.selectedProduct = this.listProduct[index];
    },
    active(index) {
      return {
        active: this.selectedProduct === this.listProduct[index]
      };
    },
    handleAddToCart() {
      this.$emit('addToCart', this.selectedProduct);
    }
  },
}  ;
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
.product-content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 5px;
  align-items: flex-start;
}
.product-details {
  display: flex;
  flex-direction: column; /* Hiển thị các phần tử theo chiều dọc */
  align-items: flex-start;
  gap: 5px;
}


.wrapper-price {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
}

.wrapper-price .final-price {
  color: #f57224;
  font-weight: 700;
}

.wrapper-price .origin-price {
  font-size: 14px;
  color: #999;
  text-decoration: line-through;
}

.wrapper-price .sale-price {
  color: white;
  background-color: red; /* Màu nền cho ô */
  padding: 5px 10px; /* Đảm bảo có padding xung quanh nội dung */
  border-radius: 10px; /* Bo tròn góc */
}

.wrapper-color {
  display: flex;
  align-items: center;
  margin-top: 15px;
  border-top: 1px solid #eee;
}

.wrapper-color .text {
  width: 100px;
}

.list-color ul {
  list-style-type: none;
  display: flex;
  padding: 0;
}

.list-color ul li {
  width: 30px;
  height: 30px;
  border: 1px solid #ccc;
  margin-right: 5px;
  border-radius: 5px;
  cursor: pointer;
  overflow: hidden;
  transition: border-color 0.3s;
}

.list-color ul li img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.list-color ul li:hover,
.list-color ul li.active {
  border-color: #f57224;
}

.product-image .image img {
  width: 100%; /* Đảm bảo ảnh chiếm toàn bộ chiều rộng của phần tử cha */
  height: auto; /* Giữ tỉ lệ khung hình */
  display: block;
  border: 1px solid #ccc;
  border-radius: 5px;
  object-fit: cover; /* Đảm bảo ảnh không bị biến dạng và lấp đầy khung */
}
.title a {
  color: #333;
  text-decoration: none;
}
</style>
