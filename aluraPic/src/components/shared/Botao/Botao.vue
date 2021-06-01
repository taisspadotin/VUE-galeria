<template>
    <button :class="estiloDoBotao" :type="tipo" @click="disparaAcao()">{{rotulo}}</button>
</template>
<script>
export default {
    props: {
        tipo: {
            required: true,
            type: String
        },
        rotulo: {
            required: true,
            type: String
        },
        confirmacao: {
            required: false,
            type: Boolean
        },
        estilo: {
            required: false,
            type: String
        }
    },
    methods: {
        disparaAcao() {
            if(this.confirmacao){
                if(confirm('Confirma operacao?')) {
                    this.$emit('botaoAtivado');
                }
                return;
            }
            this.$emit('botaoAtivado');
        }
   },

   computed:{
       estiloDoBotao(){
           if(this.estilo == "padrão") return 'botao botao-padrao';
           if(this.estilo == "perigo") return 'botao botao-perigo';
           if(this.estilo == "") return 'botao botao-padrao';
       }
   }
}
</script>    

<style scoped>
    .botao {
        display: inline-block;
        padding: 10px;
        border-radius: 5px;
        margin: 10px;
        font-size: 1.2em;
    }

    .botao-perigo {
        background: none;
        border: 2px solid #f50174;
        color: #f50174;
    }

    .botao-padrao {
        background: darkcyan;
        color: white;
    }

</style>