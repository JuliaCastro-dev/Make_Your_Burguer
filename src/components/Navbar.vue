<template>
  <nav id="nav">
    <router-link to="/" id="Logo_url">
      <img :src="logo" :alt="alt" id="Logo" />
    </router-link>
    <router-link to="/">Home</router-link>
    <router-link to="/orders">Pedidos</router-link>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"],
};
</script>

<style scoped>
#nav {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 1vw 2vw;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  height: 15vh;
}

#nav #Logo_url {
  margin: auto;
  margin-left: 0;
  overflow: hidden;
}

#Logo {
  width: 4vw;
  height: 4vw;
}
#nav a {
   color: #fcba03;
   text-decoration: none;
   margin: 0.5vw;
   transition: .5s;
      font-size: 1vw;
}

#nav a:hover {
   color: #fff;

}
</style>
