<template>
  <div>
   
      <keep-alive>
        <router-view v-if="$route.meta.keepAlive"/>
    </keep-alive>
        <router-view v-if="!$route.meta.keepAlive"/>
   

         <footers v-show="!($route.path=='/show')"></footers>
  </div>
</template>

<script>
import footers from '@/components/layout/footer'
export default {
  data () {
    return {
     
    }
  },
  mounted(){
    console.log(this.$route.path);
      this.$store.commit("vuexInit");
  },
  components:{
    footers
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    body{
      display: flex;
      .footer{
        height: r(42)

      }
      & :nth-child(1){
        flex: 1

      }

    }

</style>

