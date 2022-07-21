<template>
  <v-container>
    <h1>Cadastro de Livros</h1>
    <hr>
    <v-form>
      <v-container>
        <v-row>
          <v-col
            cols="2"
          >
            <v-text-field
              v-model="livro.id"
              placeholder="Código"
              label="Código"
              disabled
              outlined
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col 
          cols="10">
            <v-text-field
              v-model="livro.titulo"
              placeholder="titulo"
              label="titulo"
              outlined
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col 
          cols="10">
            <v-text-field
              v-model="livro.sinopse"
              placeholder="Sinopse"
              label="Sinopse"
              outlined
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col 
          cols="10">
            <v-text-field
              v-model="livro.autor"
              placeholder="Autor"
              label="Autor"
              outlined
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col 
          cols="10">
            <v-text-field
              v-model="livro.categoria"
              placeholder="Categoria"
              label="Categoria"
              outlined
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-checkbox
            v-model="padless"
            label="Emprestado"         
            />
          </v-col>
        </v-row>
      </v-container>
    </v-form>
    <v-btn
      outlined
      to="/livros"
    >
      Cancelar
    </v-btn>
    <v-btn
      outlined
      @click="cadastrar"
    >
      Cadastrar
    </v-btn>
  </v-container>
</template>

<script>
export default {
  name: 'CadastroCategoriasPage',
  data () {
    return {
      livro: {
        id: null,
        Titulo: null,
        Sinopse: null,
        Autor: null,
        Categoria: null,
        Emprestado: null
      }
    }
  },

  methods: {
    async cadastrar () {
      let livro = {
        titulo: this.livros.titulo,
        autor: this.livros.autor,
        sinopse: this.livros.sinopse,
        categoria: this.livros.categoria,
      };
      let response = await this.$axios.$post('http://localhost:3333/categorias', livro);
      // location.reload();
      console.log(response);
      alert(`Categoria ${response.nome} criada com sucesso, id ${response.id}.`)
    }
  }
}
</script>