<template>
  <div>
    <Nav :changeSort="changeSort"></Nav>
    <item v-for="item in page.data" :key="item.name" :merchant="item"></item>


    <div class="has-text-centered" v- v-show="loadding">正在加载中状态</div>
  </div>
</template>

<script>
import Nav from "./components/MerchantListNav.vue";
import Item from "./components/MerchantListItem.vue";
import Vue from "vue";

export default {
  name: "MerchantList",
  data: function() {
    let data = [];
    for (let i = 0; i < 35; i++) {
      data.push({
        logo:
          "https://tse3-mm.cn.bing.net/th?id=OIP.JN7kWG5XFVe4sLn2ATnaQQHaIo&w=194&h=160&c=7&o=5&pid=1.7",
        name: "KFC（文鼎）-" + i,
        stars: 4.5,
        sales: 877 + i * 5,
        deliveryTime: 30,
        distance: 800,
        minAmount: 3800,
        deliveryAmount: 200,
        meituanOnly: true,
        isSupportInvoice: true,
        minInvoice: 1000
      });
    }
    return {
      data: data,
      page: {
        totalCount: 0,
        totalPageNum: 0,
        pageSize: 10,
        pageNum: 1,
        data: []
      },
      //是否正在加载数据状态
      loadding: false,
      //正在加载中状态
      loadMoreing: true
    };
  },
  mounted: function() {
    this.page.totalCount = this.data.length;
    let totalCount = this.page.totalCount;
    let temp = totalCount % this.pageSize;
    let pageNum = parseInt(totalCount / this.page.pageSize)+1;
    if (temp > 0) {
      pageNum++;
    } else if (temp <= 0) {
      pageNum = 1;
    }
    this.page.totalPageNum = pageNum;
    this.getPageData();
    window.addEventListener("scroll",this.scrollFn);
  },
  methods: {
    scrollFn: function() {
      //真实内容的高度
      let pageHeight = Math.max(
        document.body.scrollHeight,
        document.body.offsetHeight
      );

      //视窗的高度
      let viewportHeight =
        window.innerHeight ||
        document.documentElement.clientHeight ||
        document.body.clientHeight ||
        0;

      //隐藏的高度
      let scrollHeight =
        window.pageYOffset ||
        document.documentElement.scrollTop ||
        document.body.scrollHeight ||
        0;

      let pos = pageHeight - viewportHeight - scrollHeight;
      if (pos < 20) {
        this.nextPage();
      }
    },
    nextPage: function() {
      //判断是否是最后一项
      if (this.page.pageNum === this.page.totalPageNum) {
        this.loadMoreing = false;
        return;
      }
      //判断是否正在加载数据
      if (this.loadding) {
        return;
      }
      //开启数据
      this.loadding = true;
      this.page.pageNum++;
      let scrollHeight = document.body.scrollHeight;
      setTimeout(() => {
        this.getPageData();
        this.loadding = false;
        Vue.nextTick(function() {
          //DOM 滚动到上次内容最后位置
          document.documentElement.scrollTop = scrollHeight;
        });
      },1000);
    },
    getPageData: function() {
      let star = this.page.pageSize * (this.page.pageNum - 1);
      let end = star + this.page.pageSize;
      if (end > this.page.totalCount) {
        end = this.page.totalCount;
      }
      const curPageData = this.data.slice(star, end);
      this.page.data = this.page.data.concat(curPageData);
    },
    changeSort: function(type) {
      if (type === 0) {
        this.page.data.sort(function(a, b) {
          return a.sales - b.sales;
        });
      } else if (type === 1) {
        this.page.data.sort(function(a, b) {
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
