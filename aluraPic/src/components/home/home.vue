<template>
  <div class="corpo">
    
    <meu-titulo :titulo="titulo">
      <div slot="conteudo">
        <h1></h1>
      </div>
    </meu-titulo>

    <div class="input-filtro">
      <input type="search" class="filtro" v-on:input="filtro = $event.target.value" placeholder="filtre pelo título da foto">
    </div>

    <div class="row-galeria">
      <div class="card" v-for="foto of fotosComFiltro">
        <card-content :foto="foto"/>
        <meu-botao 
          rotulo="remover" 
          tipo="button" 
          :confirmacao="false"
          estilo="perigo"
          @botaoAtivado="remove(foto)"/>
      </div>  
    </div>
    
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
import CardContent from '../shared/CardContent/CardContent.vue';
import Botao from '../shared/Botao/Botao.vue';
export default {
  components: {
    'meu-titulo': Painel,
    'card-content': CardContent,
    'meu-botao': Botao
  },
  methods: {
    remove(foto) {
         if(confirm('Confirma?')) {
             alert(foto.titulo);
         }
    }
  },
  data(){
    return {
      titulo: "Galeria",
      fotos:[],
      filtro: '',
      visivel: true
    }
  },
  computed: {
    fotosComFiltro() {

      if (this.filtro) {
        let exp = new RegExp(this.filtro.trim(), 'i');
        return this.fotos.filter(foto => exp.test(foto.titulo));
      } else {
        return this.fotos;
      }

    }
  },
  created(){
    this.$http.get('http://localhost:3000/v1/fotos')
      .then(resp => resp.json())
      .then(fotos => this.fotos = fotos, err => console.error(err))
  }
}
</script>

<style>
  .row-galeria{
    display: flex;
    box-sizing: border-box;
    max-width: 100%;
    overflow: auto;
    margin: 0px 20px;
    padding: 0;
  }

  .card{
    background: #fff;
    margin: 1px;
    margin-left: 8px;
    margin-bottom: 5px;
    padding: 10px;
    padding-bottom: 35px;
    border-radius: 5px;
    width: max-content;
    box-shadow: 2px 2px 2px #000;
  }

  .card p{
    color: #000;
    font-family: 'Caveat', cursive;
    font-size: 20px;
    width: 250px;
  }

  .centralizado{
    text-align: center;
    font-family: 'Caveat', cursive;
    font-size: 40px;
    font-weight: 400;
    color: #f50174;
  }

  .card img{
    width: 250px;
    height: 250px;
    border-radius: 5px;
    filter: grayscale(100%);
    cursor: pointer;
  }
  
  .card img:hover{
    filter: none;
  }

  .input-filtro{
    margin: 0px 28px;
    margin-bottom: 20px;
    width: 25%;
  }

  input{
    background: #2c2c2c;
    color: #fff;
    border: none;
    border-bottom: 2px solid #f50174;
    min-height: 35px;
    padding-left: 5px;
    width: 100%;
  }

</style>
