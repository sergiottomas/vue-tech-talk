<template>
    <div class="right-align">
      <input placeholder="Escreva uma Tarefa" id="txt_tarefa" type="text" class="left" v-model="txtTask" v-on:keyup.enter="preparedToAdd()">
      <button class="waves-effect waves-light btn" v-on:click="preparedToAdd()">
        <i class="material-icons left">add</i>
          Nova Tarefa
      </button>
    </div>
</template>

<script>
export default {
    name: "add-task",
    data() {
        return {
            txtTask: ""
        }
    },
    methods: {
        preparedToAdd() {
            this.$emit('preparedToAdd', {
                name: this.txtTask,
                description: ""
            })

            this.txtTask = "";
        }
    }
}
</script>
