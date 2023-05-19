<template>
  <div class="author-form">
    <div class="author-inputs">
      <div class="input-wrapper">
        <label for="name">Nome:</label>
        <input type="text" id="name" v-model="author.name" required />
      </div>
      <div class="input-wrapper">
        <label for="surname">Sobrenome:</label>
        <input type="text" id="surname" v-model="author.surname" required />
      </div>
    </div>
    <p v-if="!author.name || !author.surname" class="error-message">
      O campo do autor é obrigatório.
    </p>
    <button @click="addCoAuthor">Adicionar Coautor</button>
    <div
      v-for="(coauthor, index) in coauthors"
      :key="index"
      class="coauthor-inputs"
    >
      <h3>Coautor {{ index + 1 }}</h3>
      <div class="input-wrapper">
        <label :for="'coauthorName' + index">Nome:</label>
        <input
          type="text"
          :id="'coauthorName' + index"
          v-model="coauthor.name"
          required
        />
      </div>
      <div class="input-wrapper">
        <label :for="'coauthorSurname' + index">Sobrenome:</label>
        <input
          type="text"
          :id="'coauthorSurname' + index"
          v-model="coauthor.surname"
          required
        />
      </div>
      <button @click="removeCoAuthor(index)">Remover Coautor</button>
    </div>
    <button @click="redirectToNextPage">Próximo</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      author: {
        name: '',
        surname: '',
      },
      coauthors: [],
    };
  },
  methods: {
    addCoAuthor() {
      this.coauthors.push({ name: '', surname: '' });
    },
    removeCoAuthor(index) {
      this.coauthors.splice(index, 1);
    },
    redirectToNextPage() {
      if (this.author.name && this.author.surname) {
        // Realizar ações necessárias antes de redirecionar
        this.$router.push('/outra-tela');
      } else {
        alert('Por favor, preencha todos os campos do autor.');
      }
    },
  },
};
</script>

<style>
.author-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #f2f2f2;
}

.author-inputs {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.input-wrapper {
  margin: 0 10px;
}

.coauthor-inputs {
  margin-top: 20px;
}

.error-message {
  color: red;
  margin-top: 5px;
}

button {
  background-color: #4caf50;
  color: #fff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
  border-radius: 4px;
}

button:hover {
  background-color: #45a049;
}

input[type='text'] {
  padding: 8px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 14px;
  width: 200px;
}

label {
  font-weight: bold;
  margin-right: 5px;
}
</style>
