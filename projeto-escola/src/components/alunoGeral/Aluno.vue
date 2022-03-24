<template>
  <div>
    <TituloG titulodDsc="descrição do titulo" />

    <div>
      <input
        type="text"
        placeholder="Nome do Aluno"
        v-model="qualquercoisa"
        v-on:keyup.enter="addAlunos()"
      />
      <button @click="addAlunos()">adicionar</button>
    </div>

    <table>
      <thead>
        <th>matricula</th>
        <th>nome</th>
        <th>opçoes</th>
      </thead>
      <tbody>
        <tr v-for="(aluno, index) in alunos" :key="index">
          <td>{{ aluno.id}}</td>
          <td>{{ aluno.nome }}</td>
          <td><button class="btn" @click="remover(aluno)">remover</button></td>
        </tr>
      </tbody>
      <tfoot v-if="!alunos.length">
        nenhum aluno encontrado
      </tfoot>
    </table>
  </div>
</template>
<script>
import TituloG from "../tituloGeral/Titulo.vue";
export default {
  components: {
    TituloG,
  },
  data() {
    //aqui é necessario exportar algo e essa data pode ser qualquer coisa
    return {
      qualquercoisa: "Aluno",
      alunos: [],
      descricao: "aprendendo vueJS",
    };
  },
  created() {
    this.$http
      .get("http://localhost:3000/alunos")
      .then(res => res.json())
      .then(res=>this.alunos = res);

  },
  methods: {
    remover(aluno) {
      this.$http
      .delete(`http://localhost:3000/alunos/${aluno.id}`).then(()=>{
          let indice = this.alunos.indexOf(aluno);
        this.alunos.splice(indice, 1)
      })
      
    },
    addAlunos() {
      let _aluno = {
        nome: this.qualquercoisa,
        matricula: 0
      };
      this.$http.post("http://localhost:3000/alunos",_aluno).then(res=>res.json())
      this.alunos.push(_aluno);
    },
  },
};
</script>
<style scoped>
body {
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}
body,
html {
  margin: 0;
  height: 100%;
}
#app {
}

table {
  margin: 0px;
  padding: 0px;
  list-style-type: none;
  width: 100%;
}
table tr td {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
}
table thead th {
  background-color: rgb(184, 208, 216) !important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}
.colPequeno {
  width: 5%;
}
.btn {
  background-color: #fa4430;
  padding: 10px 20px;
  cursor: pointer;
  color: white;
  font-weight: bold;
  border-radius: 10px;
  border-bottom: 4px solid black;
}
.btn:hover {
  text-shadow: 1px 1px 1px black;
  border-bottom: 1px solid black;
  margin-top: 3px;
}
</style>