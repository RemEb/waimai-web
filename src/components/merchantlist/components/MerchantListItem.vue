<template>
    <div>
        <article class="media">
            <div class="media-left">
                <figure class="image is-96x96">
                    <img :src="merchant.logo" alt="">
                </figure>
            </div>

            <div class="media-content" style="font-size:12px">
                <strong>{{merchant.name}}</strong>
                <div class="level is-mobile">
                    <div class="level-left has-text-warning">
                        <div>
                            <span v-for="item in getStars.starNum" :key="item" class="icon is-small">
                                <i class="fas fa-star"></i>
                            </span>

                            <span v-for="item in getStars.halfStarNum" :key="'h'+item"
                             class="icon is-small">
                                <i class="fas fa-star-half"></i>
                            </span>
                            
                            <span v-for="item in getStars.noStarNum" :key="'n'+item"
                            class="icon is-small star-black">
                                <i class="fas fa-star"></i>
                            </span>
                            <span>月售{{merchant.sales}}</span>
                        </div>
                    </div>
                    <div class="level-right">
                        <div>
                            <span>{{merchant.deliveryTime}}min</span> | <span>{{formatDistance}}</span>
                        </div>
                    </div>
                </div>
                <div class="level is-mobile">
                    <div class="level-left">
                        <span>起送价￥{{formatMinAmount}}</span> | <span>配送￥{{formatDeliveryAmount}}</span>
                    </div>
                    <div class="level-right">
                        <span class="tag is-warning">美团专送</span>
                    </div>
                </div>
                <div class="level is-mobile" style="margin-top:10px;">
                    <div class="level-left">
                        <img src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3862530009,1441346643&fm=200&gp=0.jpg" alt="" class="image is-16x16">
                        <span>本店支持开发票,开票金额最小为￥{{formatMinInvoice}}</span>
                    </div>
                </div>
            </div>
        </article>
    </div>
</template>


<script>
export default {
  name: "MerchantListItem",
  props:["merchant"],
  computed: {
    formatMinAmount: function() {
      return this.merchant.minAmount / 100;
    },
    formatDeliveryAmount: function() {
      return this.merchant.deliveryAmount / 100;
    },
    formatDistance: function() {
      if (this.merchant.distance < 1000) {
        return this.merchant.distance + "m";
      } else {
        return this.merchant.distance / 1000 + "km";
      }
    },
    formatMinInvoice: function() {
      return this.merchant.minInvoice / 100;
    },
    getStars: function() {
      var starNum = parseInt(this.merchant.stars);
      var halfStarNum = Number.isInteger(this.merchant.stars) ? 0 : 1;
      var noStarNum = 5 - starNum - halfStarNum;

      return {
        starNum,
        halfStarNum,
        noStarNum
      };
    }
  }
};
</script>

<style  scoped>
.level {
  margin-bottom: 0px;
  font-size: 12px;
}
.media {
  margin: 8px;
}
.star-black {
  color:dimgrey;
}
</style>
