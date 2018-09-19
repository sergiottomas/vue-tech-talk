<template>
  <div id="app" class="container">
    <list-tasks></list-tasks>

    <div v-if="taskToEdit">
      <h1>Editar Tarefa</h1>
      <div class="right-align">
        <input placeholder="Escreva uma Tarefa" id="txt_tarefa" type="text" class="left" v-model="taskToEdit.name">
        <button class="waves-effect waves-light btn" v-on:click="saveTask()">
          <i class="material-icons left">save</i>
            Salvar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
//https://api.myjson.com/bins/nsvk0
import listTasks from "./components/list-tasks"

export default {
  name: "app",
  components: {
    listTasks
  },
  data() {
    return {
      taskToEdit: null
    };
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
