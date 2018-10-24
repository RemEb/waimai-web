<template>
    <div>
        <nav class="level is-mobile">
            <div class="level-item has-text-centered">
                <div class="level-item">
                    <span class="nav-title">美食</span>
                    <span class="icon">
                        <i class="fas fa-angle-down"></i>
                    </span>
                </div>
                <div class="level-right">
                    |
                </div>
            </div>

            <div class="level-item has-text-centered">
                <div class="level-item" @click="openSort(true)">
                    <span class="nav-title">综合排序</span>
                    <span class="icon">
                        <i class="fas fa-angle-down"></i>
                    </span>
                </div>
                <div class="level-right">
                </div>
            </div>

            <div class="level-item has-text-centered">
                <div class="level-item">
                    <span class="nav-title">筛选</span>
                    <span class="icon">
                        <i class="fas fa-filter"></i>
                    </span>
                </div>

            </div>
        </nav>
        <Sort :isShow="isSortShow" :changeSort="callbackChangeSort"></Sort>
        <div class="shadow" @click="openSort(false)" :style="getShow"></div>
        <div class="tabs">
            <ul></ul>
        </div>
    </div>
</template>

<script>
import Sort from "./SortDropdown.vue";
export default {
  name: "MerchantListNav",
  props:["changeSort"],
  data:function(){
      return {
          isSortShow:false,
      }
  },
  computed:{
    getShow:function(){
        if(this.isSortShow) {
            return "display:block";
        }else{
            return "display:none";
        }
    }
  },
  methods:{
      openSort:function(isOpen) {
          this.isSortShow = isOpen;
      },
      callbackChangeSort:function(type) {
          this.changeSort(type);
          this.isSortShow = false;
      }
  },
  components:{
      Sort,
  }
};
</script>

<style scoped>
.level {
  margin: 10px;
}
.nav-title {
  font-size: 13px;
}
.icon {
  font-size: 12px;
}

.shadow {
  position: absolute;
  top: 50px;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 19;
  background: rgba(0, 0, 0, 0.5);
}
</style>
