<template>
  <div>
    <meu-titulo titulo="Cadastro"/>
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
export default {
  components: {
    'meu-titulo': Painel
  }
}

</script>
<style scoped>
    .centralizado {
        text-align: center;
    }
</style>