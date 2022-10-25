<template>
  <div>
    <Message :message="message" v-show="message" />
    <div>
      <form id="burguer-form" method="post" @submit="createBurguer">
        <div class="input-container">
          <label for="name">Name</label>
          <input
            type="text"
            name="name"
            id="name"
            v-model="clientName"
            placeholder="Digite seu Nome"
          />
        </div>
        <div class="input-container">
          <label for="bread">Select the bread:</label>
          <select name="bread" v-model="clientBread" id="bread">
            <option value="">Select the bread</option>
            <option :value="bread.tipo" v-for="bread in breads" :key="bread.id">
              {{ bread.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat">Select the meat:</label>
          <select name="meat" v-model="clientMeat" id="meat">
            <option class="option" value="">Select the meat</option>
            <option
              class="option"
              :value="meat.tipo"
              v-for="meat in meats"
              :key="meat.id"
            >
              {{ meat.tipo }}
            </option>
          </select>
        </div>
        <div class="optional-container">
          <label id="optional-label" for="optional">Select the optional:</label>
          <div
            class="checkbox-container"
            v-for="optional in optionalList"
            :key="optional.id"
          >
            <input
              type="checkbox"
              name="optional"
              id="optional"
              v-model="clientOptional"
              :value="optional.tipo"
            />
            <span>{{ optional.tipo }}</span>
          </div>
        </div>
        <div class="input-container">
          <input type="submit" value="Criar" class="submit-btn" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Message from "./Message.vue";
export default {
  name: "BurguerForm",
  components: {
    Message,
  },
  data() {
    return {
      breads: null,
      meats: null,
      optionalList: null,
      clientName: null,
      clientBread: null,
      clientMeat: null,
      clientOptional: [],
      message: null,
    };
  },
  methods: {
    clearClient() {
      this.clientBread = "";
      this.clientMeat = "";
      this.clientName = "";
      this.clientOptional = "";
    },
    async getIngredients() {
      const request = await fetch("http://localhost:3000/ingredientes");
      const data = await request.json();

      this.meats = data.carnes;
      this.breads = data.paes;
      this.optionalList = data.opcionais;
    },
    async createBurguer(event) {
      event.preventDefault();
      const data = JSON.stringify({
        nome: this.clientName,
        carne: this.clientMeat,
        pao: this.clientBread,
        opcionais: Array.from(this.clientOptional),
        status: "Solicitado",
      });
      const request = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: data,
      });

      this.message = "Pedido realizado com sucesso!";
      setTimeout(() => this.message = null, 2000);
      this.clearClient();
    },
  },
  mounted() {
    this.getIngredients();
  },
};
</script>

<style scoped>
#burguer-form {
  max-width: 20vw;
}
.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 2vh;
}

label {
  font-weight: 700;
  margin-bottom: 1vh;
  color: #222;
  padding: 1.5%;
  border-left: 4px solid #fcba03;
}

#optional-label {
  width: 100%;
}

input,
select {
  padding: 3% 3%;
  width: 20vw;
  border-radius: 5px;
  outline: none;
  border: 1px solid rgb(166, 166, 166);
}

.option {
  padding: 0px;
}

.optional-container {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.checkbox-container input {
  width: auto;
  margin-right: 20px;
}

.checkbox-container input:checked {
  color: #fcba03;
}

.checkbox-container span {
  width: 100%;
}

.checkbox-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 40%;
  margin: 2%;
}

#burguer-form > div:nth-child(5) > input {
  background-color: #111;
  color: #fcba03;
  font-weight: bold;
  font-size: 1.2vw;
  text-transform: capitalize;
  margin-top: 3%;
  cursor: pointer;
}
</style>
