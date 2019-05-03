<template>
  <ul id="taskList">
    <header-section></header-section>
    <task-item v-for="(task, index) in tasks" :key="index" :task="task" :index="index" @deleteTask="deleteTask"></task-item>
    <manager-task-add v-show="hasAddTaskManagerOpen" @addTask="addTask" @cancelTask="cancelTask" @saveTask="saveTask"></manager-task-add>
    <task-item-button-add
      class="tasks"
      @click.native="openAddTaskManager"
      v-show="!hasAddTaskManagerOpen"
    ></task-item-button-add>
  </ul>
</template>

<script>
import TaskItemButtonAdd from "./TaskItemButtonAdd.vue";
import ManagerTaskAdd from "./ManagerTaskAdd.vue";
import TaskItem from "./TaskItem.vue";
import HeaderSection from "./HeaderSection.vue";

export default {
  data() {
    return {
      hasAddTaskManagerOpen: false,
      tasks: []
    };
  },
  components: {
    TaskItemButtonAdd,
    ManagerTaskAdd,
    TaskItem,
    HeaderSection,
  },
  methods: {
    openAddTaskManager() {
      this.hasAddTaskManagerOpen = true;
    },
    addTask(task) {
      this.tasks.push(task);
      this.hasAddTaskManagerOpen = false;
    },
    cancelTask(task) {
      this.hasAddTaskManagerOpen = false;
    },
    deleteTask(index) {
      this.tasks.splice(index,1);
    },
    saveTask(task){
      this.$set(this.tasks, task.index, task)
    }
  },
  mounted() {
    if (localStorage.tasks) {
      this.tasks = JSON.parse(localStorage.getItem("tasks"));
    }
  },
  watch: {
    tasks(newTasks) {
      localStorage.setItem("tasks", JSON.stringify(newTasks));
    }
  }
};
</script>

<style scoped>
#taskList {
  list-style-type: none;
  width: 600px;
}
</style>


