<template>
    <div class="product">
        <img :src="oneroom.image" alt="">
        <h4 @click="$emit('openModal',i)">{{ oneroom.title }}</h4>
        <p>{{oneroom.price}}원</p>
  </div>
</template>

<script>

export default {
    name : 'ProductCard',
    props : {
        oneroom : Array,
    }
}
</script>

<style>

</style>