<template>
    <div class="black-bg">
      <div class="white-bg">
        <img :src="oneroom.image" alt="">
        <h4>{{ oneroom.title }}</h4>
        <p>{{ oneroom.content }}</p>
        <input v-model.number="month" >
        <p>{{month}}개월 거주시 :  {{ oneroom.price * month }}원</p>
        <button @click="$emit('closeModal')">닫기</button>
      </div>
    </div>
</template>

<script>

export default {
  name : 'OpenModal',

  data(){
    return{
      month : 1,
    }
  },
  
  watch : {
    month(after) {
      if ( isNaN(after) || after<0 || after>13 ){
        alert('a');
        this.month = 1
      }
    }
  },

  updated(){
    if(this.month==2){
      alert('3개월이상만가능');
      this.month=3;
    }
  },

  props : {
    oneroom : Object,
  }
}
</script>

<style>

</style>