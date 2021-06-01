<template>
  <div class="corpo">

    <meu-menu :rotas="routes"/>
    <router-view/>

  </div>
</template>

<script>
import { routes }  from './routes';
import Menu from './components/shared/Menu/Menu.vue';
export default {
  components: {
    'meu-menu' : Menu
  },
  data() {

    return {

      routes
    }

  }

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Caveat:wght@400;500&display=swap');
  
  .corpo{
    font-family: Arial, Helvetica, sans-serif;
    width: 100%;
    margin: 0;
    color: #fff;
  }

  body{
    margin: 0;
    background: #2c2c2c;    
  }

</style>