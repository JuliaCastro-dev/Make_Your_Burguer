<template>
  <Banner/>
  <div class="main-container">
    <h1> Monte seu Hambúrguer do seu jeito ;)</h1>
    <BurguerForm/>
  </div>
</template>

<script>
import Banner from '../components/Banner.vue'
import BurguerForm from '../components/BurguerForm.vue'

export default {
  components:{
    Banner,
    BurguerForm
  }
}

</script>

<style scoped>
.main-container {
  overflow-y: auto;
  align-items: center;
  justify-content: center;
  display: flex;
  flex-direction: column;
}

h1{
  width:100%;
  text-align: center;
}
</style>
