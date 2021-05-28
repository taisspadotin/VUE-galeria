<template>
<div>
    <h1 class="titulo">{{ titulo }}</h1>
    <slot name="conteudo" class="conteudo"></slot> <!-- para pegar o que vai dentro do componente criado-->
</div>
</template>

<script>
export default {
   props: ['titulo']
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Caveat:wght@400;500&display=swap');
    .titulo{
    text-align: center;
    font-family: 'Caveat', cursive;
    font-size: 40px;
    font-weight: 400;
    color: #fff;
    text-shadow: 0px 0px 10px #f50174;
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0% {
      color: #cfcdcd !important;
      text-shadow: 0px 0px 0px #f50174;
    }
    25% {
      text-shadow: 0px 0px 5px #f50174;
    }
    50% {
      text-shadow: 0px 0px 10px #f50174;
    }
    75% {
      text-shadow: 0px 0px 15px #f50174;
    }
    100% {
      text-shadow: 0px 0px 20px #f50174;
    }
  }
</style>
