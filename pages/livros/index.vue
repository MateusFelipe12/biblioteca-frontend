<template>
  <v-container>
    <h1 style="color:aquamarine ;">Consulta de Livros</h1>
    <hr>
    <v-container>
      <v-row>
        <v-col>
          <v-btn
            outlined
            @click="getLivros"
          >
            Pesquisar
          </v-btn>
        </v-col>
        <v-col>
          <v-btn
            outlined
            to="/livros/cadastro"
          >
            Cadastrar
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
    <v-container>
      <v-data-table
        :headers="headers"
        :items="livros"
        :items-per-page="all"
        class="elevation-1"
      ></v-data-table>
    </v-container>
  </v-container>
</template>

<script>
export default {
  name: 'ConsultaLivrosPage',
  data () {
    return {
      headers: [
        {
          text: 'Código', 
          align: 'center', 
          sortable: false, 
          value: 'id',
        },
        {
          text: 'Titulo',
          align: 'center',
          sortable: false,
          value: 'titulo',
        },  
        {
          text: 'Sinopse',
          align: 'center',
          sortable: false,
          value: 'sinopse'
        },
        {
          text: 'Autor', 
          align: 'center', 
          sortable: false, 
          value: 'idAutor',
        },  
        {
          text: 'Categoria', 
          align: 'center', 
          sortable: false, 
          value: 'idCategoria',
        },  
        {
          text: 'Emprestado', 
          align: 'center', 
          sortable: false, 
          value: 'emprestado',
        },
      ],
      livros: []
    }
  },
  created () {
    this.getLivros ()
  },
  methods: {
    async getLivros () {
      let livros = await this.$axios.$get('http://localhost:3333/livros');
      this.livros = livros.data.livros
      console.log(livros.data);
    }
  }
}
</script>
