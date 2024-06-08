<template>
  <header>
    <div class="header-container">
      <div class="logo">Livan Sport</div>
      <div class="welcome-message">
        Chào mừng bạn đến với Livan Sport ! Khám phá bộ sưu tập mới nhất của chúng tôi!
      </div>
      <div class="nhap-nhay-hieu-ung" :class="{ 'nhap-nhay': dangNhapNhay }">
        <i class="fas fa-exclamation-circle"></i> Miễn phí vận chuyển cho đơn hàng từ 500,000 VNĐ trở lên!
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderWeb',
  data() {
    return {
      dangNhapNhay: true
    };
  },
  mounted() {
    this.dangNhapNhay = true;
  }
};
</script>

<style scoped>
header {
  background-color: #FFB6C1;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 10px 20px;
}

.header-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.logo {
  font-size: 1.5em;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 10px;
}
.logo:hover {
  color: #FF69B4;
  transform: scale(1.1);
}

.welcome-message {
  font-size: 1.2em;
  color: darkcyan;
  margin-bottom: 10px;
  font-weight: bold;
  white-space: nowrap; /* Ngăn chữ xuống dòng */
  overflow: hidden; /* Ẩn phần vượt quá giới hạn */
  animation: slideRight 20s linear infinite; /* Di chuyển từ bên trái sang phải trong 10 giây và lặp lại vô hạn */
}

@keyframes slideRight {
  0% {
    transform: translateX(-100%); /* Di chuyển sang bên trái */
  }
  100% {
    transform: translateX(100%); /* Di chuyển sang bên phải */
  }
}

.nhap-nhay-hieu-ung {
  font-weight: bold;
  color: #ff7e5f;
}
.nhap-nhay {
  animation: nhap-nhay-hieu-ung 1s steps(5, start) infinite;
}

@keyframes nhap-nhay-hieu-ung {
  to {
    visibility: hidden;
  }
}
</style>
