<script lang="ts">
import {obterCategorias} from '@/http/index'
import type ICategorias from '@/interfaces/ICategorias'
import CardCategoria from './CardCategoria.vue';
export default {
    data(){
        return {
            categorias: [] as ICategorias[]
        }
    },
    components: {
      CardCategoria
    },

    async created(){
        this.categorias = await obterCategorias()
    }
}
</script>
<template>
    <section class="selecionar-ingredientes">
        <h1 class="cabecalho titulo-ingredientes">
            Ingredientes
        </h1>
        <p class="paragrafo-lg instrucoes">
            Selecione abaixo os ingredientes que você quer usar neesta receita.
        </p>
        <ul class="categoria">
            <li v-for="categoria in categorias" :key="categoria.nome">
                <CardCategoria :categoria="categoria"/>
            </li>
        </ul>
        <p class="paragrafo dica">
            Atenção: consideramos que você tenha em casa sal, pimenta e água.
        </p>
    </section>
</template>
<style scoped>

.categoria {
  display: flex;
  flex-wrap: wrap
}

.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #FFFAF3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}

.sua-lista-texto {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.ingredientes-sua-lista {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}

.ingrediente {
  display: inline-block;
  border-radius: 0.5rem;
  min-width: 4.25rem;
  padding: 0.5rem;
  text-align: center;
    transition: 0.2s;
    color: var(--creme, #FFFAF3);
  background: var(--coral, #F0633C);
  font-weight: 700;
}

.lista-vazia {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #F0633C);
  text-align: center;
}

@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}
</style>