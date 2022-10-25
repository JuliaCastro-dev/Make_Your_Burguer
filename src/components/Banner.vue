<template>
<div id="main-banner">
   <h1> Make Your Burguer</h1>
</div>
</template>

<script>
export default {
   name:'Banner'
}
</script>


<style scoped>
#main-banner {
   background-image: url("/public/img/burguer.jpg");
   background-position: 0 -15vh;
   background-size: cover;
   background-repeat: no-repeat;
   width: 100%;
   height: 85vh;
   display: flex;
   align-items: center;
   justify-content: flex-start;
}
#main-banner h1 {
   color: #fff;
   text-align: center;
   font-size: 4vw;
   padding: 1vw 3vw;
}
</style>