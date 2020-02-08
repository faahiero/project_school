# Projeto Sistema Acadêmico Simples

O intuito desta pequena aplicação é de ser um sistema acadêmico, para universidades ou escolas.
Como trata-se apenas de um protótipo, temos somente as telas de Professores e Alunos, onde pode-se 
cadastrar Professores, vincular Alunos à eles, bem como remover ambos. Também é possível editar, de
maneira simplificada, as informações dos alunos vinculados a um determinado professor, assim como
trocá-lo de professor.

## Rodando a aplicação

Certifique-se de possuir instalado em sua máquina o NodeJS, seu gerenciador de pacotes, o NPM e 
o Dotnet Core 2.2.

1. Executando o Front-End (VueJS)

  - Instale os pacotes necessários com o comando:

```bash
npm install
```
  - Execute a aplicação:
  
```bash
npm run serve
```

2. Executando o Back-End (Dotnet Core 2.2)

  - Restaure os pacotes necessários com o comando:

```bash
dotnet restore
```

  - Execute a aplicação:
  
```bash
dotnet run
```


