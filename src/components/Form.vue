<template>
  <div>
    <p>Componente de Mensagem</p>
    <div>
      <form id="burger-form">
        <div class="input-container">
          <label for="name">Nome do cliente</label>
          <input type="text" id="name" name="name" v-model="name" placeholder="Digite o seu nome">
        </div>
        <div class="input-container">
          <label for="bread">Escolha o pão:</label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option value="integral">Integral</option>
          </select>
        </div>
        <div class="input-container">
          <label for="bread">Escolha a carne do seu Burguer:</label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Selecione o tipo de carne</option>
            <option value="maminha">Maminha</option>
          </select>
        </div>
        <div class="input-container">
          <label for="bread">Selecione os opcionais:</label>
          <div class="checkbox-container">
            <input type="checkbox" name="optional" v-model="optional" value="salame">
            <span>Salame</span>
          </div>
        </div>
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Criar meu Burguer!">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Form",
};
</script>
