<template>
  <div>
    <h1>{{ qualquercoisa }}</h1>
    <input
      type="text"
      placeholder="Nome do Aluno"
      v-model="qualquercoisa"
      v-on:keyup.enter="addAlunos()"
    />
    <table border="1px">
      <thead>
        <th>matricula</th>
        <th>nome</th>
        <th>opçoes</th>
      </thead>
      <tbody>
        <tr v-for="(aluno, index) in alunos" :key="index">
          <td>{{ aluno.matricula + 3 }}</td>
          <td>{{ aluno.nome }}</td>
          <td><button class="btn" @click="remover">remover</button></td>
        </tr>
      </tbody>

      <thead></thead>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    //aqui é necessario exportar algo e essa data pode ser qualquer coisa
    return {
      qualquercoisa: "Aluno",
      alunos: [
        { matricula: 1, nome: "moises" },
        { matricula: 2, nome: "Rafael" },
        { matricula: 3, nome: "carla" },
      ],
    };
  },
  methods: {
    remover() {
      let indice = this.alunos.indexOf(this.aluno);
      this.alunos.splice(indice, 1);
    },
    addAlunos() {
      let _aluno = {
        nome: this.qualquercoisa,
      };
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
  border-bottom: 3px solid black;
}
.btn:hover {
  text-shadow: 1px 1px 1px black;
  border-bottom: 1px solid black;
  margin-top: 2px;
}
</style>