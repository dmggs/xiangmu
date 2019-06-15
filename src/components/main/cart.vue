<template>
  <div id="cart">
    <ul class="cart">
      <li v-for="(item,index) in $store.state.shopCart.list" :key="index" class="carts">
        <div class="top">
          <div class="left">
            <img src="https://res.bestcake.com/m-images/order/mw_firm_duihao_2.jpg">
          </div>
          <div class="right">
            <div class="right1">
              <img :src="item.url"  @click="toShow(item.name,item.Brand)">
            </div>
            <div class="right2">
              <div class="item-name">{{item.name|textLengthSet(10)}}</div>
              <div class="right3">
                <div class="item-size">{{item.size}}</div>
                <div class="item-num">
                  <span @click="del(index)">-</span>
                  <span>{{item.num}}</span>
                  <span @click="add(index)">+</span>
                </div>
              </div>
              <div class="right4">
                <span>{{item.num*item.price}}.00</span>
              </div>
            </div>
          </div>
        </div>
        <div class="heng" v-show="!(index%2==0)"></div>
        <div class="botton">
          <p>
            <span>优惠方式</span>不参与活动
          </p>
        </div>
      </li>
    </ul>
    <div>
      <p>Hot  Recommend</p>
      <p>热销新品推荐</p>
    </div>
    <div class="dibu">
      <div class="one">
        <img src="https://res.bestcake.com/m-images/order/mw_firm_duihao_2.jpg" class="img">
        <span>全选</span>
        <span @click="clear">清空</span>
      </div>
      <div class="two">
        合计:
        <span style="color:red;font-weight:bolder;">{{cunt}}</span>
        <div style="font-weight: bolder">已优惠:0.00</div>
      </div>
      <div class="three">结算</div>
    </div>
  </div>
</template>

<script>
import { MessageBox } from "mint-ui";
export default {
  data() {
    return {
      list: []
    };
  },
  methods: {
    toShow(key, c) {
      this.$router.push({
        path: "/show",
        query: { key, c }
      });
    },
    add(index) {
      var data=this.$store.state.shopCart.list[index]
       this.$store.commit("jia",data);
     
    },
    del(index) {
      var data=this.$store.state.shopCart.list[index]
       this.$store.commit("jian",data);
      // }
    },
    clear(){
       MessageBox.confirm("", {
        message: "是否清空购物车?",
      
        confirmButtonText: "确定",
        cancelButtonText: "取消"
      })
        .then(action => {
          if (action == "confirm") {
            //确认的回调
            this.$store.commit("clear")
          }
        })
        .catch(err => {
          if (err == "cancel") {
            //取消的回调
          }
        });
       
    },
    quanxun() {}
  },
  mounted() {},
  computed: {
    cunt() {
      var p = 0;
      this.$store.state.shopCart.list.forEach(element => {
        p += element.num * element.price;
      });
      return p;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
 <style scoped lang="scss">
#cart {
  .cart {
    .carts {
      border-bottom: r(12) solid #f7f7f7;
      .heng {
        background: #ccc;
        width: r(270);
        height: r(1);
        margin-left: r(50);
      }
      .botton {
        padding: r(10) 0;
        padding-left: r(50);
        span {
          color: #f2495e;
          font-weight: bolder;
        }
      }
      .top {
        display: flex;
        .left {
          img {
            width: r(17);
            height: r(17);
            text-align: center;
            margin-top: r(50);
            margin-left: r(12);
          }
        }
        .right {
          display: flex;
          width: r(206);
          height: r(104);
          .right1 {
            img {
              width: r(97);
              height: r(92);
              margin-top: r(10);
              margin-left: r(12);
            }
          }
          .right2 {
            margin-left: r(10);
            .item-name {
              font-size: r(13);
              width: r(156);
              line-height: r(26);
              margin-top: r(10);
            }
            .right3 {
              display: flex;
              justify-content: space-between;
              .item-size {
                color: #ccc;
              }
              .item-num {
                font-size: r(15);
                span {
                  padding: r(2) r(5);
                }
              }
            }
            .right4 {
              font-size: r(13);
              font-weight: bolder;
              line-height: r(45);
            }
          }
        }
      }
    }
  }
  .dibu {
    position: fixed;
    top: r(478);
    display: flex;
    background: #fff;
    height: r(48);
    justify-content: space-between;
    width: 100%;
    .one {
      .img {
        width: r(17);
        height: r(17);

        margin-left: r(5);
      }
      span {
        line-height: r(48);
        padding: 0 r(5);
        font-size: r(13);
      }
    }
    .two {
      line-height: r(22);
    }
    .three {
      line-height: r(48);
      width: r(98);
      height: r(48);
      background: #02d4d7;
      color: #fff;
      font-weight: bolder;
      text-align: center;
      font-size: r(16);
    }
  }
}
</style>


