
<template>
  <div class="cart">
    <i class="fas fa-shopping-cart"></i>
    Giỏ hàng ({{ cardNumber }})
  </div>
</template>

<script >
import '@fortawesome/fontawesome-free/css/all.css';
export default {
  name: 'xe-day',
  props: {
    cardNumber: Number,
  },
};

</script>



<style scoped>
.cart {
  display: inline-block;
  padding: 10px 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
}
</style>