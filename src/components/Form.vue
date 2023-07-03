<template>
  <div>
    <p>Componente de Mensagem</p>
    <div>
      <form id="burger-form">
        <div class="input-container">
          <label for="name">Nome do cliente</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            placeholder="Digite o seu nome"
          />
        </div>
        <div class="input-container">
          <label for="bread">Escolha o pão:</label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option v-for="bread in paes" :key="bread.id" :value="bread.tipo">{{ bread.tipo }}</option>
          </select>
        </div>
        <div class="input-container">
          <label for="bread">Escolha a carne do seu Burguer:</label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Selecione o tipo de carne</option>
            <option value="maminha">Maminha</option>
          </select>
        </div>
        <div id="optional-container" class="input-container">
          <label id="optional-title" for="optional"
            >Selecione os opcionais:</label
          >
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="optional"
              v-model="optional"
              value="salame"
            />
            <span>Salame</span>
          </div>
        </div>
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Criar meu Burguer!" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisdata: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: "Solicitado",
      msg: null,
    };
  },
  methods: {
    async getIngredients() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisdata = data.opcionais;
    },
  },
  mounted() {
    this.getIngredients();
  },
};
</script>

<style scoped>
#burger-form {
  max-width: 400px;
  margin: 0 auto;
}
.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#optional-container {
  flex-direction: row;
  flex-wrap: wrap;
}

#optional-title {
  width: 100%;
}

.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox-container span,
.checkbox-container input {
  width: auto;
}

.checkbox-container span {
  margin-left: 6px;
  font-weight: bold;
}

.submit-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
  border-radius: 6px;
}

.submit-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>
