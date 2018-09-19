<template>
  <div id="app" class="container">
    <h1>Lista de Tarefas</h1>

    <div class="right-align">
      <input placeholder="Escreva uma Tarefa" id="txt_tarefa" type="text" class="left">
      <button class="waves-effect waves-light btn">
        <i class="material-icons left">add</i>
          Nova Tarefa
      </button>
    </div>

    <ul class="collection">
      <li class="collection-item">
        <div>
           <label>
            <input type="checkbox"  />
            <span>Estudar Vue</span>
          </label>
          
          <a href="#!" class="secondary-content">
            <i class="material-icons">delete</i>
          </a>
        </div>
      </li>

      <li class="collection-item">
        <div>
           <label>
            <input type="checkbox"  />
            <span>Analisar meus códigos</span>
          </label>
          
          <a href="#!" class="secondary-content">
            <i class="material-icons">delete</i>
          </a>
        </div>
      </li>

      <li class="collection-item">
        <div>
           <label>
            <input type="checkbox"  />
            <span>Reunião com Chefia</span>
          </label>
          
          <a href="#!" class="secondary-content">
            <i class="material-icons">delete</i>
          </a>
        </div>
      </li>

      <li class="collection-item">
        <div>
           <label>
            <input type="checkbox"  />
            <span>Estudar Ingles</span>
          </label>
          
          <a href="#!" class="secondary-content">
            <i class="material-icons">delete</i>
          </a>
        </div>
      </li>
    </ul>

    <p>Concluidas: 0</p>

    <p class="alert">Você não possúi nenhuma Tarefa</p>

    <h1>Editar Tarefa</h1>
    <div class="right-align">
      <input placeholder="Escreva uma Tarefa" id="txt_tarefa" type="text" class="left" value="Estudar Vue">
      <button class="waves-effect waves-light btn">
        <i class="material-icons left">save</i>
          Salvar
      </button>
    </div>

    <div class="col s12 m7">
    <h2 class="header">Estudar Ingles</h2>
    <div class="card horizontal">
      <div class="card-stacked">
        <div class="card-content">
          <textarea>
            Preciso Estudar Ingles, usando os livros que estão na biblioteca da Av XYZ
          </textarea>
        </div>
        <div class="card-action right-align">
          <a href="#">Salvar</a>
          <a href="#">Remover</a>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
//https://api.myjson.com/bins/nsvk0
export default {
  name: "app",
  data() {
    return {
      tasks: []
    };
  },
  methods: {
    addNewTask() {
      this.tasks.push();
    }
  }
};
</script>

<style lang="scss">

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

#add-task-button {
  position: absolute;
  bottom: 100px;
  right: 100px;
}

label {
  color: #333;
}

textarea {
  border: none;
  resize: none;
}
</style>
