<template>
  <div class="container">
    <h1>Gerentes</h1>
    <div class="row">
      <Gerente
        v-for="gerente in gerentes"
        :key="gerente.numero"
        :gerente="gerente"
      />
    </div>
  </div>
</template>

<script>
import Gerente from "@/components/Gerente.vue";

export default {
  components: {
    Gerente,
  },
  data() {
    return {
      gerentes: [],
    };
  },
  mounted() {
    this.$http
      .get("gerentes")
      .then((response) => (this.gerentes = response.data))
      .catch((err) => console.log(err));
  },
  beforeRouterEnter(to, from, next) {
    if (!this.$store.state.token) {
      next({ name: "login" });
    }
    next();
  },
};
</script>

<style>
</style>