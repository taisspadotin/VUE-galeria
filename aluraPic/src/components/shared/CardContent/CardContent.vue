<template>
<div>
    <div @dblclick="visivel = !visivel"><!--função de duplo clique (@ substitui v-on)-->
        <transition name="painel-fade">
            <img :src="foto.url" :alt="foto.titulo" v-show="visivel"/>
        </transition>
    </div>
    <p>{{foto.titulo}}</p>
</div>
</template>

<script>
export default {
    props: ['foto'],
    data(){
        return {
            visivel: true
        }
    }
}
</script>

<style>
.painel-fade-enter, .painel-fade-leave-active {
  opacity: 0
}

.painel-fade-enter-active, .painel-fade-leave-active {
  transition: opacity .4s
}
</style>
