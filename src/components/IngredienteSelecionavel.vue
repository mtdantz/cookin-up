<script lang="ts">
import Tag from './Tag.vue';
export default {
    components:{
        Tag,
    },
    props:{
        ingrediente: { type: String, required:true} //Sempre que uma tag estiver um v-bind de outro component, precisamos trazer ele dentro de uma props, com o type dele e o required: true
    },
    data(){
        return{
            selecionado: false
        }
    },
    methods: {
    aoClicar() {
      this.selecionado = !this.selecionado

      if (this.selecionado) {
        this.$emit('adicionarIngrediente', this.ingrediente)
      } else {
        this.$emit('removerIngrediente', this.ingrediente);
      }
    }
  },
  emits: ['adicionarIngrediente', 'removerIngrediente']

}

</script>

<template>

    <button class="ingrediente" @click="aoClicar"> 
        <!-- Nesta conjuntura, o @click vai trazer o selecionado e receber o valor inverso dele, para dar o efeito de seleção e 'des'seleção -->
        <Tag :texto="ingrediente" :ativa="selecionado" />
    </button>

</template>

<style scoped>
.ingrediente{
    cursor: pointer;
}

</style>