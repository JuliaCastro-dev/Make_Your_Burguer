<template>
  <div id="burguer-table">
    <div>
      <div id="burguer-table-heading">
        <div class="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Adicionais:</div>
        <div>Ações:</div>
      </div>
      <div id="burguer-table-rows">
        <div class="burguer-table-row" v-for="burguer in burguers" :key="burguer.id">
          <div class="order-number">{{ burguer.id }}</div>
          <div>{{ burguer.nome }}</div>
          <div>{{ burguer.pao }}</div>
          <div>{{ burguer.carne }}</div>
          <div>
            <ul>
              <li>Maionese veg</li>
              <li>Tomate</li>
            </ul>
          </div>
          <div>
            <select name="status" class="status">
              <option>Selecione</option>
            </select>
          </div>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  data(){
    return{
      burguers:null,
      burguer_id:null,
      status:[]
    }
  },
  methods: {
    async getOrders(){
      const request = await fetch("http://localhost:3000/burgers");
      this.burguers = request.json();
    }
  },
  mounted(){
    this.getOrders();
  }

};
</script>

<style scoped>
#burguer-table {
  max-width: 80vw;
  margin: 0 auto;
}
#burguer-table-heading,
#burguer-table-rows,
.burguer-table-row {
  display: flex;
  flex-wrap: wrap;
}

#burguer-table-heading {
  font-weight: 700;
  padding: 12px;
  border-bottom: 3px solid rgb(119, 119, 119);
}

#burguer-table-heading div,
.burguer-table-row div {
  width: 19%;
}

.burguer-table-row {
  width: 100%;
  padding: 12px;
  flex-wrap: nowrap;
  flex-direction: row;
  border-bottom: 1px solid #ccc;
}

#burguer-table-heading .order-id,
.burguer-table-row .order-number {
  width: 5%;
}

select {
  padding: 12px 6px;
  margin-right: 12px;
}

.delete-btn {
  background-color: crimson;
  color: aliceblue;
  font-weight: 800;
  padding: 10px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
  border: 3px solid aliceblue;
  border-radius: 5px;
  font-size: 0.7vw;
}
.delete-btn:hover {
  background-color: rgb(255, 255, 255);
  color: crimson;
  border: 3px solid crimson;
}
</style>
