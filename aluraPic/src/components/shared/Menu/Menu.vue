<template>
    <nav class="menu">
      <ul>       
          <li v-for="rota in rotas">
            <router-link :to="rota.path ? rota.path : '/'">{{rota.titulo}}</router-link>
          </li>
      </ul>
    </nav>

</template>
<script>
export default {

    props: {
        rotas: {
            type: Array, 
            required: true
        }
    }
}
</script>    

<style scoped>
.menu{
    background: #ffffff30;
    border-bottom: 2px solid #f50174;
    
}
.menu ul{
    display: flex;
    padding: 0;
    margin: 0;
    padding: 15px 20px;
}
.menu li{
    width: auto;
    margin-left: 10px;
    margin-right: 10px;
    list-style: none;
}
.menu a{
    text-decoration: none;
    color: #f1f1f1;
    font-weight: 600;
}
.menu a:hover{
    color: #fff;
}
</style>