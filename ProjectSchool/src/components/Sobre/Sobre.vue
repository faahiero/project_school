<template>
  <div>
    <titulo texto="Sobre" btnVoltar="true" />
    <p>
      O intuito desta pequena aplicação é de ser um sistema acadêmico, para universidades ou escolas.
      Como trata-se apenas de um protótipo, temos somente as telas de Professores e Alunos, onde pode-se
      cadastrar Professores, vincular Alunos à eles, bem como remover ambos. Também é possível editar, de
      maneira simplificada, as informações dos alunos vinculados a um determinado professor, assim como
      trocá-lo de professor.
    </p>
  </div>
</template>

<script>
import Titulo from "../_share/Titulo";

export default {
  components: {
    Titulo
  }
};
</script>

<style scoped>
p {
  text-align: justify;
  line-height: 25px;
}
</style>