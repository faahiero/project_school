<template>
  <div>
    <titulo texto="Professores" btnVoltar="true" />
    <input type="text" placeholder="Nome do Professor" v-model="nome" @keyup.enter="addProfessor()" />
    <button class="btn btnInput" @click="addProfessor()">Adicionar</button>
    <table>
      <thead>
        <th>Cód.</th>
        <th>Nome</th>
        <th>Alunos</th>
        <th>Opções</th>
      </thead>
      <tbody v-if="Professores.length">
        <tr v-for="(professor, index) in Professores" :key="index">
          <td class="colPequeno">{{professor.id}}</td>

          <router-link
            :to="`/alunos/${professor.id}`"
            tag="td"
            style="cursor: pointer"
          >{{professor.nome}} {{professor.sobrenome}}</router-link>

          <td class="colPequeno">{{professor.qtdAlunos}}</td>
          <td class="colPequeno">
            <Button class="btn btn_Danger" @click="remover(professor)">Remover</Button>
          </td>
        </tr>
      </tbody>
      <tfoot v-else>
        <tr>
          <td colspan="4" style="text-align: center">
            <h5>Nenhum Professor Encontrado</h5>
          </td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
import Titulo from "../_share/Titulo";

export default {
  components: {
    Titulo
  },
  data() {
    return {
      nome:"",
      Professores: [],
      Alunos: []
    };
  },
  created() {
    this.$http
      .get("http://localhost:5000/api/aluno")
      .then(res => res.json())
      .then(alunos => {
        this.Alunos = alunos;
        this.carregarProfessores();
      });
  },
  props: {},
  methods: {
    pegarQtdAlunosPorProfessor() {
      this.Professores.forEach((professor, index) => {
        professor = {
          id: professor.id,
          nome: professor.nome,
          qtdAlunos: this.Alunos.filter(
            aluno => aluno.professor.id == professor.id
          ).length
        };
        this.Professores[index] = professor;
      });
    },
    carregarProfessores() {
      this.$http
        .get("http://localhost:5000/api/professor")
        .then(res => res.json())
        .then(professor => {
          this.Professores = professor;
          this.pegarQtdAlunosPorProfessor();
        });
    },
    addProfessor() {
      let _prof = {
        nome:this.nome
      };

      this.$http
        .post("http://localhost:5000/api/professor", _prof)
        .then(res => res.json())
        .then(prof => {
          this.Professores.push(prof);
          this.nome = "";
        });
    },
    remover(professor) {
      this.$http.delete(`http://localhost:5000/api/professor/${professor.id}`).then(() => {
        let indice = this.Professores.indexOf(professor);
        this.Professores.splice(indice, 1);
      });
    }
  }
};
</script>

<style scoped>
.colPequeno {
  text-align: center;
  width: 15%;
}

.btnInput {
  width: 150px;
  border: 0px;
  padding: 20px;
  font-size: 1.3em;
  display: inline;
  background-color: rgb(116, 115, 115);
}

input {
  width: calc(100% - 195px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  color: #687f7f;
  display: inline;
}
</style>