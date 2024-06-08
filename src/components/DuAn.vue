<template>
  <div>
    <div class="container">
      <div id="app">
        <XeDay :cardNumber="cardNumber" />
        <SanPham
            :listProduct="danhSachSanPham"
            :sanPhamDaChon="sanPhamDaChon"
            :price="giaTien"
            :sale="giaGIam"
            @addToCart="handleAddToCart"
        />
        <div class="description">
          <ul class="extra-info">
            <li v-for="(item, index) in listDesc" :key="index">{{ item }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import XeDay from '@/components/XeDay.vue';
import SanPham from '@/components/SanPham.vue';


export default {
  name: 'Du_An',
  components: {
    XeDay,
    SanPham,
  },
  data() {
    return {
      cardNumber: 1,
      sanPhamDaChon: 2,
      giaGIam: 0.2,
      giaTien : 200000,
      danhSachSanPham: [
        {
          image: require('@/assets/red.jpg'),
          quantity: 5,
          textColor: 'Màu Đỏ',
        },
        {
          image: require('@/assets/blue.jpg'),
          quantity: 8,
          textColor: 'Màu Xanh',
        },
        {
          image: require('@/assets/black.jpg'),
          quantity: 2,
          textColor: 'Màu Đen',
        },
        {
          image: require('@/assets/white.jpg'),
          quantity: 0,
          textColor: 'Màu Trắng',
        },
        {
          image: require('@/assets/yellow.jpg.webp'),
          quantity: 7,
          textColor: 'Màu Vàng',
        }
      ],
      listDesc: [
        'Chất liệu: polyester và thun',
        'Thoát mồ hôi tốt',
        'Áo thun cổ tròn thể thao Hiye chuyên được may từ chất liệu nilon thoáng mát',
        'Kết hợp thêm sợi thun tạo độ co giãn giúp người tiêu dùng thoải mái khi mặc',
        'Chất liệu: polyester và thun'
      ],
    };
  },
  methods: {
    handleAddToCart(product) {
      if (this.cardNumber + 1 > product.quantity) {
        alert('Hiện tại số lượng không đủ');
      } else {
        this.cardNumber += 1;
      }
    },
  }
};
</script>


<style scoped>
/* Reset CSS */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #f7f7f7;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 30px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
.description {
  max-width: 700px;
}

.description .extra-info li {
  padding-left: 20px; /* Điều chỉnh khoảng cách lùi đầu dòng */
  text-indent: -20px; /* Điều chỉnh khoảng cách lùi đầu dòng của chữ */
  text-align: left; /* Căn các dòng chữ về bên trái */
  color: #f57224;
}
header, footer {
  color: #fff;
  padding: 15px 30px;
  margin: 0;
}

header {
  background-color: #3498db;
}

footer {
  background-color: #34495e;
}

header h1, footer h1 {
  margin: 0;
}
</style>

