<template>
  <div>
     <img :src="logo">
      <img v-bind:src="'/vue-cli-demo/static/images/'+Img+'.jpg'" v-bind:alt="Img" />
      <img v-bind:src="SrcImg"   v-bind:alt="Img" />
      <button v-on:click="imgAdd">img++</button>
      <button v-on:click="imgReduce">img--</button>
      <p>{{id}}</p>
  </div>
</template>
<script>

export default {
  data () {
    return {
      id: this.$route.params.id,
      logo: require('@/assets/logo.png')
    }
  },
  methods: {
    imgAdd: function () {
      if (!this.id) {
        this.id = 1
      }
      if (this.id < 3) {
        this.id++
      } else {
        this.id = 1
      }
      this.$router.push({ path: `/img/${this.id}` })
    },
    imgReduce: function () {
      if (this.id > 1) {
        this.id--
      } else {
        this.id = 3
      }
      this.$router.push({ path: `/img/${this.id}` })
    }
  },
  computed: {
    SrcImg () {
      // console.log('aa:', location)
      if (this.id) {
        return '/vue-cli-demo/static/images/' + this.id + '.jpg'
      } else {
        return '/vue-cli-demo/static/images/1.jpg'
      }
    },
    Img () {
      if (this.id) {
        return this.id
      } else {
        return '1'
      }
    }
  }

/*   created(){
      console.log(this.$route)
      if(!this.$route.params){
        this.src = "../src/assets/1.jpg";
      }
       this.src = "../src/assets/"+this.$route.params.id+".jpg"
  }, */
/*   watch:{
     '$route' (to, from) {
          this.src="../static/images/"+this.$route.params.id+".jpg"
      }
  } */
}
</script>
<style scoped>
img{
    width: 100px;
}
</style>
