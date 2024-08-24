<template>

<transition name="fade">
    <openModal
    v-if="viewModal==true"
    :oneroom="onerooms[clickProduct]"
    @closeModal="viewModal=false"/>
  </transition>

  <div class="menu">
    <a href="" v-for="(menu,i) in menus" :key="i">{{i+1}} {{menu}}</a>
  </div>    

  <discount v-if="discountShow==true" :discountPersent="discountPersent"/>

  <div class="sortButton">
    <button @click="priceSort2()">가격순내림차순</button>
    <button @click="priceSort()">가격순오름차순</button>
    <button @click="sortBack()">정렬되돌리기</button>
  </div>

  <productCard 
    v-for="(oneroom,i) in onerooms" :key="i" 
    :oneroom="oneroom" 
    @openModal="viewModal=true; clickProduct=i;"/>
  
</template>

<script>

import onerooms from './assets/onerooms';
import discount from './components/DiscountProduct.vue'
import productCard from './components/ProductCard.vue';
import openModal from './components/OpenModal.vue'


export default {
  name: 'App',
  data(){
    return{
      oneroomsOrigin : [...onerooms],
      onerooms : onerooms,
      menus : ['Home', 'Shop','About'],
      viewModal : false,
      clickProduct : 0,
      discountPersent : 30,
      discountShow : true,
    }
  },

  methods :  {
    increase(i) {
      this.report[i]+=1
    },
    priceSort(){
      this.onerooms.sort(function(a,b){
        return a.price-b.price
      });
    },
    priceSort2(){
      this.onerooms.sort(function(a,b){
        return b.price-a.price
      });
    },
    sortBack(){
      this.onerooms = [...this.oneroomsOrigin];
    },
  },
  mounted(){                     
    setInterval(() => {
      if(this.discountPersent>0){
        this.discountPersent--;
      }
     }, 1000);
  },
  updated(){

  },
  components: {
    discount,
    openModal,
    productCard,
  }
}
</script>

<style>
*{
  margin: 0;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
  text-align: center;
}
.menu a{
  color: white;
  padding: 10px;
  }
.discount{
 color: #000;
}
.product{
  border: black 2px solid;
  padding: 1rem;
  margin: 1rem;
  width: 900px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}
.product img{
  width: 600px;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 50%; background-color: white;
  border-radius: 8px;
  padding: 20px;
  margin: auto;
  text-align: center;
}
.fade-enter-from{
opacity: 0;
}
.fade-enter-active{
transition: all 0.5s;
}
.fade-enter-to{
opacity: 1;
}
.fade-leave-from{
opacity: 1;
}
.fade-leave-active{
transition: all 0.5s;
}
.fade-leave-to{
opacity: 0;
}
.sortButton{
  text-align: center;
}
</style>
