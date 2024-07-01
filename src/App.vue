<script setup>
import { reactive, ref } from 'vue'

const titulo = ref('Digite algo ...')
const mostrarResultado = ref(false)
const produto = reactive({
  nome: '',
  email: '',
  senha: '',
  senhar: '',
  estado: [],
  hobbie: [],
})
const estados = [
  { id: 'AC', name: 'Acre' },
  { id: 'AL', name: 'Alagoas' },
  { id: 'AP', name: 'Amapá' },
  { id: 'AM', name: 'Amazonas' },
  { id: 'BA', name: 'Bahia' },
  { id: 'CE', name: 'Ceará' },
  { id: 'DF', name: 'Distrito Federal' },
  { id: 'ES', name: 'Espírito Santo' },
  { id: 'GO', name: 'Goiás' },
  { id: 'MA', name: 'Maranhão' },
  { id: 'MT', name: 'Mato Grosso' },
  { id: 'MS', name: 'Mato Grosso do Sul' },
  { id: 'MG', name: 'Minas Gerais' },
  { id: 'PA', name: 'Pará' },
  { id: 'PB', name: 'Paraíba' },
  { id: 'PR', name: 'Paraná' },
  { id: 'PE', name: 'Pernambuco' },
  { id: 'PI', name: 'Piauí' },
  { id: 'RJ', name: 'Rio de Janeiro' },
  { id: 'RN', name: 'Rio Grande do Norte' },
  { id: 'RS', name: 'Rio Grande do Sul' },
  { id: 'RO', name: 'Rondônia' },
  { id: 'RR', name: 'Roraima' },
  { id: 'SC', name: 'Santa Catarina' },
  { id: 'SP', name: 'São Paulo' },
  { id: 'SE', name: 'Sergipe' },
  { id: 'TO', name: 'Tocantins' }
];
const hobbies = [{ id: 'Futebol', name: 'Futebol' },
{ id: 'Ler', name: 'Ler' },
{ id: 'Desenhar', name: 'Desenhar' },
{ id: 'Jogar Videogame', name: 'Jogar Videogame' },];
</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="container">
    <div class="formulario">
      <h2>Formulario</h2>
      <input type="text" v-model="titulo">
      <hr>
      <div class="row">
        <label for="nome">Nome: </label>
        <input type="text" v-model="produto.nome">
      </div>
      <div class="row">
        <label for="email">E-mail: </label>
        <input type="email" v-model="produto.email">
      </div>
      <div class="row">
        <label for="senha">Senha: </label>
        <input type="password" v-model="produto.senha">
      </div>
      <div class="row">
        <label for="senhar">Senha confirma: </label>
        <input type="password" v-model="produto.senhar">
      </div>
      <div class="row">
        <label for="dnasc">Data de Nascimento: </label>
        <input type="date" v-model="produto.dnasc">
      </div>
      <div class="row">
        <label for="enderoco">Endereço: </label>
        <input type="text" v-model="produto.enderoco">
      </div>
      <fieldset>
        <legend>Estados</legend>
        <div v-for="estado in estados" :key="estado.id">
          <input type="checkbox" v-model="produto.estado" :value=estado.id>{{ estado.name }}
        </div>
      </fieldset>
      <fieldset>
        <legend>Hobbies</legend>
        <div v-for="hobbie in hobbies" :key="hobbie.id">
          <input type="checkbox" v-model="produto.hobbie" :value=hobbie.id>{{ hobbie.name }}
        </div>

      </fieldset>
      <button @click="mostrarResultado = !mostrarResultado">Enviar</button>

    </div>
    <Trasintion>
      <div v-if="mostrarResultado" class="resultado">
        <h2>Resultado</h2>
        <h3>dados do produtos</h3>
        <p>Nome: {{ produto.nome }}</p>
        <p>E-mail {{ produto.email }}</p>
        <p>Senha: {{ produto.senha }}</p>
        <p>Data de Nascimento: {{ produto.dnasc }}</p>
        <p>Endereço: {{ produto.enderoco }}</p>
        <p>Estado: {{ produto.estado }}</p>
        <p>Hobbies: {{ produto.hobbie }}</p>
        <p>{{ mostrarResultado }}</p>
      </div>
    </Trasintion>

  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  column-gap: 2rem;
}

.formulario,
.resultado {
  min-height: 80vh;
  width: 46vw;
  border-radius: 10px;
  padding: 10px;
}

.formulario {
  background-color: rgb(175, 161, 37);
}

.resultado {
  background-color: rgb(52, 206, 14);
}

h2 {
  margin: 0;
  padding: 0;
}

.row {
  margin-bottom: 4px;
}
</style>