<script>
import Tag from './Tag.vue'
export default {

    emits: ['adicionarIngredientes', 'removerIngredientes'],

    data(){
        return {
            selecionado: false
        }
    },

    props: {
        ingrediente: {
            type: String,
            required: true
        }
    },

    components: {
        Tag
    },

    methods: {
        aoClicar(){
            this.selecionado = !this.selecionado
            if(this.selecionado){
                this.$emit('adicionarIngrediente', this.ingrediente)
                return
            }
            
            this.$emit('removerIngrediente', this.ingrediente)
        }
    }
}
</script>
<template>
    <button
        class="ingrediente"
        :aria-pressed="selecionado"
        @click="aoClicar">
        <Tag :texto="ingrediente" :ativa="selecionado"/>
    </button>
</template>

<style scoped>
.ingrediente{
    cursor: pointer;
}
</style>