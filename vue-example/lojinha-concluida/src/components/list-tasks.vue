<template>
    <div>
        <div v-if="taskToEdit === null">
            <h1>Lista de Tarefas</h1>
            <add-task v-on:preparedToAdd="addNewTask"></add-task>
            <div v-if="tasks.length > 0">
                <ul class="collection">
                    <li class="collection-item" v-for="(task, index) in tasks">
                        <div>
                            <label>
                                <input type="checkbox"  v-on:change="finishTask($event, task)" :checked="task.isChecked ? 'checked' : ''"/>
                                <span>{{ task.name }}</span>
                            </label>

                            <a href="#!" class="secondary-content" v-on:click="deleteTask(index)">
                                <i class="material-icons">delete</i>
                            </a>

                            <a href="#!" class="secondary-content" v-on:click="editTask(task, index)">
                                <i class="material-icons">edit</i>
                            </a>
                        </div>
                    </li>
                </ul>

                <p>Concluidas: {{ tasksFinished }} / {{ tasks.length }}</p>
            </div>

            <p class="alert" v-if="tasks.length === 0">Você não possúi nenhuma Tarefa</p>
        </div>

        <edit-task v-if="taskToEdit" :selectedTask="taskToEdit" @finishEditTask="saveTask"></edit-task>
    </div>
</template>

<script>
import addTask from "./add-task";
import editTask from "./edit-task";

export default {
    data() {
        return {
            tasks: [],
            tasksFinished: 0,
            taskToEdit: null
        }
    },
    components: {
        addTask,
        editTask
    },
    methods: {
        addNewTask(newTask) {
            this.tasks.push(newTask);
        },
        deleteTask(index) {
            this.tasks.splice(index, 1);
            this.updateTasksFinished();
        },
        finishTask(ev, task) {
            if (ev.target.checked) {
                task.isChecked = true;
            } else {
                task.isChecked = false;
            }

            this.updateTasksFinished();
        },
        updateTasksFinished() {
            this.tasksFinished = this.tasks.reduce((sum, task) => {
                let finished = 0;

                if (task.isChecked) {
                finished = 1;
                }

                return sum + finished;
            }, 0)
        },
        editTask(task, index) {
            this.taskToEdit = {
                task: task,
                index: index
            };
        },
        saveTask(params) {
            this.taskToEdit = null;
            this.tasks[params.index] = params.newTask;
        }
    }
}
</script>

