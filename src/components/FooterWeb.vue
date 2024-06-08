<template>
  <footer class="footer">
    <div class="footer-links">
<!--      hiển thị khi bạn di chuột qua liên kết.-->
      <div class="home page">
      <a href="https://livansport.com/">TRANG CHỦ</a>
      </div>
      <div class="support">
      <a>HỖ TRỢ KHÁCH HÀNG</a>
      <ul class="links">
        <li><a href="https://livansport.com/tin-tuc/huong-dan-mua-hang-online-n899.html">Hướng dẫn mua hàng online</a></li>
        <li><a href="https://livansport.com/tin-tuc/chinh-sach-doi-tra-hang-n900.html">Chính sách đổi trả</a></li>
        <li><a href="https://livansport.com/tin-tuc/phuong-thuc-thanh-toan-n901.html">Phương thức thanh toán</a></li>
      </ul>
      </div>
    </div>
    <div class="address">
      <p>ĐỊA CHỈ: Số 356, Đường Giải Phóng, Thành phố Hà Nội</p>
      <p>Email: fashion@gmail   .com</p>
      <p>Điện thoại: 0 999 66 686</p>
    </div>
    <div class="social-icons">
      <a href="https://www.facebook.com/livansport/"><i class="fab fa-facebook-f"></i></a>
      <a href="https://www.youtube.com/c/livansport"><i class="fab fa-youtube"></i></a>
      <a href="https://shopee.vn/livansport"><i class="fas fa-shopping-cart"></i></a>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterWeb',

}
</script>

<style scoped>
footer {
  background-color: #f2f2f2;
  padding: 20px 0;
}


.footer {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.footer-links {
  display: flex;
  align-items: center; /* Canh các phần tử theo chiều dọc */
  margin-left: 40px;
}

.footer-links a {
  margin-right: 20px;
  color: #333;
  font-weight: bold;
}


.footer-links .support {
  margin-left: 40px; /* Khoảng cách giữa phần "Trang chủ" và "Hỗ trợ khách hàng" */
}


.links {
  display: flex;
  flex-direction: column;
  align-items: start;
  margin: 0;
  padding: 0;
}

.sub-links li {
  display: inline;
}

.sub-links a {
  text-decoration: none;
  color: #666;
  font-size: 14px;
}

.sub-links a:hover {
  color: #f57224;
}
.social-icons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
}

.social-icons a {
  font-size: 24px;
  color: inherit;
  text-decoration: none;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #f0f0f0;
}
</style>
