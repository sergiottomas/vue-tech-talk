<template>
    <div>
        <h1>Editar Tarefa</h1>
        <div class="right-align">
            <input placeholder="Escreva uma Tarefa" id="txt_tarefa" type="text" class="left" v-model="txtTask">
            <button class="waves-effect waves-light btn" v-on:click="saveTask()">
            <i class="material-icons left">save</i>
                Salvar
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "edit-task",
    props: ["selectedTask"],
    data() {
        return {
            txtTask: ""
        }
    },
    mounted() {
        this.txtTask = this.selectedTask.task.name;
    },
    methods: {
        saveTask(task) {
            this.$emit("finishEditTask", {
                newTask: {
                    name: this.txtTask
                },
                index: this.selectedTask.index
            });

            this.taskToEdit = null;
        }
    }
}
</script>

