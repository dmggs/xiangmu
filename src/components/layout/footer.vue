<template>
  <div class="footer">
    <ul> 
      <li>
        <router-link to="/index">
             <img :src="this.$route.path=='/index'?'https://res.bestcake.com/m-images/ww/foot/foot-menu-a-2.png?v=119':'https://res.bestcake.com/m-images/ww/foot/foot-menu-a-1.png?v=119'" alt="">
        </router-link>
      
      </li>
      <li>
        <router-link to="/list">
             <img :src="this.$route.path=='/list/zy/jd'||this.$route.path=='/list/zy/ns'||this.$route.path=='/list/zy/bsl'
             ||this.$route.path=='/list/bs/rp'
             ?'https://res.bestcake.com/m-images/ww/foot/foot-menu-b-2.png?v=119':'https://res.bestcake.com/m-images/ww/foot/foot-menu-b-1.png?v=119'" alt="">
        </router-link>
      
      </li>
        <li>
        <router-link to="/cart">
           <img :src="this.$route.path=='/cart'?'https://res.bestcake.com/m-images/ww/foot/foot-menu-c-2.png?v=119':'https://res.bestcake.com/m-images/ww/foot/foot-menu-c-1.png?v=119'" alt="">
        </router-link>
        <span class="cart1" v-show="!($store.state.shopCart.nums==0)" >{{$store.state.shopCart.list.length}}</span>
        <span class="cart"></span>
      </li>
        <li>
        <router-link to="/my">
           <img :src="this.$route.path=='/my'?'https://res.bestcake.com/m-images/ww/foot/foot-menu-d-2.png?v=119':'https://res.bestcake.com/m-images/ww/foot/foot-menu-d-1.png?v=119'" alt="">
        </router-link>
      
      </li>
      
    </ul>
    <div>
    
    </div>
  </div>
</template>

<script>
export default {
 
  data () {
    return {
      bool:false,
      listindex:0,
      // list:[             
      //   {path:'/index',src1:'https://res.bestcake.com/m-images/ww/foot/foot-menu-a-1.png?v=119',src2:'https://res.bestcake.com/m-images/ww/foot/foot-menu-a-2.png?v=119'},
      //   {path:'/list',src1:'https://res.bestcake.com/m-images/ww/foot/foot-menu-b-1.png?v=119',src2:'https://res.bestcake.com/m-images/ww/foot/foot-menu-b-2.png?v=119'},
      //   {path:'/cart',src1:'https://res.bestcake.com/m-images/ww/foot/foot-menu-c-1.png?v=119',src2:'https://res.bestcake.com/m-images/ww/foot/foot-menu-c-2.png?v=119'},
      //   {path:'/my',src1:'https://res.bestcake.com/m-images/ww/foot/foot-menu-d-1.png?v=119',src2:'https://res.bestcake.com/m-images/ww/foot/foot-menu-d-2.png?v=119'}
       
      // ]
      
     
    }
  },
  methods: {
      selectindex(index){
        // document.getElementsByClassName()
       
       
        
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
 <style scoped lang="scss">


.footer{
  .cart1{
    position: fixed;
    bottom: r(30);
    left: r(210);
    width: r(14);
    height: r(14);
    background: red;
    display: inline-block;
    line-height: r(15);
    text-align: center;
    border-radius: 50%;
    color: #ffffff;
  }
  background: #ffffff;
  position: fixed;
  bottom: 0;
  
   width:100%;
    height:r(31);
  ul{
   
    display: flex;
    justify-content:space-around;
     width:100%;
    height:r(31);
    li{
      img{
        width:r(28);
        height:100%
      }
    }

  }
}

</style>









