<template>
  <div>
    <h1>Formulário de Autores</h1>
    <AuthorForm @coauthor-added="addCoAuthor" />
    <div v-for="(coauthor, index) in coauthors" :key="index">
      <h3>Coautor {{ index + 1 }}</h3>
      <p>Nome: {{ coauthor.name }}</p>
      <p>Sobrenome: {{ coauthor.surname }}</p>
    </div>
  </div>
</template>

<script>
import AuthorForm from './components/AuthorForm.vue';

export default {
  components: {
    AuthorForm,
  },
  data() {
    return {
      coauthors: [],
    };
  },
  methods: {
    addCoAuthor(coauthor) {
      this.coauthors.push(coauthor);
    },
  },
};
</script>
