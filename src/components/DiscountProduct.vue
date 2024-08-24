<template>
  <div class="discount">
     <h4>지금 결제하시면 {{discountPersent}}% 할인</h4>
  </div>
</template>

<script>
export default {
  name : 'DiscountBanner',
  props : {
    discountPersent : Number,
  }
}
</script>

<style>
  .discount{
    text-align: center;
    margin: 2rem;
  }
</style>