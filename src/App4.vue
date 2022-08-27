<template>
  <div>
    <Shop v-for="(item, index) in goodsArr" :key="index" :obj="item" />
    <p>All Number:{{ sumNumber }}</p>
  </div>
</template>

<script>
import Shop from "./components/shop.vue";
export default {
  data() {
    return {
      goodsArr: [
        {
          count: 0,
          goodsName: "Watermelon",
        },
        {
          count: 0,
          goodsName: "Banana",
        },
        {
          count: 0,
          goodsName: "Orange",
        },
        {
          count: 0,
          goodsName: "Pineapple",
        },
        {
          count: 0,
          goodsName: "Strawberry",
        },
      ],
    };
  },
  components: {
    Shop,
  },
  computed: {
    sumNumber() {
      console.log(1);
      return this.goodsArr.reduce((sum, obj) => (sum += obj.count * 1), 0);
    },
  },
};
</script>

<style></style>
