<template>
  <div class="container">
    <h1>Novo usuário</h1>
    <form @submit.prevent="enviarForm">
      <div class="form-group">
        <label for="nome">Nome</label>
        <input
          name="nome"
          type="text"
          class="form-control"
          v-model="usuario.nome"
        />
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input
          name="email"
          type="email"
          class="form-control"
          v-model="usuario.email"
        />
      </div>

      <div class="form-group">
        <label for="senha">Senha</label>
        <input
          name="senha"
          type="password"
          class="form-control"
          v-model="usuario.senha"
        />
      </div>
      <button class="btn btn-primary" type="submit">Salvar</button>
    </form>
  </div>
</template>

<script>
// import axios from "axios";

export default {
  data: function () {
    return {
      usuario: {
        nome: "",
        email: "",
        senha: "",
      },
    };
  },
  methods: {
    enviarForm() {
      this.$http
        .post("auth/register", this.usuario)
        .then((resposta) => {
          console.log(resposta);
          this.$router.push({ name: "login" });
        })
        .catch((erro) => console.log(erro));
    },
  },
};
</script>

<style></style>
