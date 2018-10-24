<template>
  <div>
    <Nav :changeSort="changeSort"></Nav>
    <item v-for="item in merchants" :key="item.name" :merchant="item"></item>

  </div>
</template>

<script>
import Nav from "./components/MerchantListNav.vue";
import Item from "./components/MerchantListItem.vue";

export default {
  name: "MerchantList",
  data: function() {
    return {
      merchants: [
        {
          logo:
            "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
          name: "KFC（文鼎）",
          stars: 4.5,
          sales: 877,
          deliveryTime: 30,
          distance: 800,
          minAmount: 3800,
          deliveryAmount: 200,
          meituanOnly: true,
          isSupportInvoice: true,
          minInvoice: 1000
        },{
          logo:
            "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
          name: "KFC（文鼎）2",
          stars: 4.5,
          sales: 877,
          deliveryTime: 30,
          distance: 800,
          minAmount: 3800,
          deliveryAmount: 200,
          meituanOnly: true,
          isSupportInvoice: true,
          minInvoice: 1000
        },{
          logo:
            "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
          name: "KFC（文鼎）",
          stars: 4.5,
          sales: 77,
          deliveryTime: 30,
          distance: 800,
          minAmount: 3800,
          deliveryAmount: 200,
          meituanOnly: true,
          isSupportInvoice: true,
          minInvoice: 1000
        },{
          logo:
            "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
          name: "KFC（文鼎）",
          stars: 4.5,
          sales: 8717,
          deliveryTime: 30,
          distance: 800,
          minAmount: 3800,
          deliveryAmount: 200,
          meituanOnly: true,
          isSupportInvoice: true,
          minInvoice: 1000
        },{
          logo:
            "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
          name: "KFC（文鼎）",
          stars: 4.5,
          sales: 837,
          deliveryTime: 30,
          distance: 800,
          minAmount: 3800,
          deliveryAmount: 200,
          meituanOnly: true,
          isSupportInvoice: true,
          minInvoice: 1000
        },{
          logo:
            "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
          name: "KFC（文鼎）",
          stars: 4.5,
          sales: 37,
          deliveryTime: 30,
          distance: 800,
          minAmount: 3800,
          deliveryAmount: 200,
          meituanOnly: true,
          isSupportInvoice: true,
          minInvoice: 1000
        },{
          logo:
            "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
          name: "KFC（文鼎）",
          stars: 4.5,
          sales: 877,
          deliveryTime: 30,
          distance: 800,
          minAmount: 3800,
          deliveryAmount: 300,
          meituanOnly: true,
          isSupportInvoice: true,
          minInvoice: 1000
        }
      ]
    };
  },
  methods:{
    changeSort:function(type) {
      if(type === 0) {
        this.merchants.sort(function(a,b) {
          return a.sales - b.sales;
        });
      }else if(type === 1) {
        this.merchants.sort(function(a,b) {
          return b.sales - a.sales;
        });
      }
    }
  },
  components: {
    Nav,
    Item
  }
};
</script>

<style scoped>


</style>
