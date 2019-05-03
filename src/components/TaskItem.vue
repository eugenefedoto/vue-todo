<template>
  <li
    class="task_item not_shared menu_clickable priority_1 agenda_item indent_1 item_3178380724"
    id="item_3178380724"
    v-if="!amEditingTask"
  >
    <div class="invisible_space"></div>
    <table cellpadding="0" cellspacing="0">
      <tbody>
        <tr>
          <td class="checker sel_checkbox_td">
            <div class="ist_checkbox" @click="deleteTask">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
                <path d="M20.285 2l-11.285 11.567-5.286-5.011-3.714 3.716 9 8.728 15-15.285z"></path>
              </svg>
            </div>
          </td>
          <td class="text_cursor content task_content_item">
            <div style="display:flex; justify-content: space-between">
              <div @click="editTaskName">{{taskInstance.name}}</div>
              <div>{{task.date}}</div>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </li>
  <li v-else>
    <manager-name-edit :taskName="task.name" :dateProp="task.date" @saveTask="saveTask" @cancelTask="cancelTask"></manager-name-edit>
  </li>
</template>

<script>
import ManagerNameEdit from "./ManagerNameEdit.vue";

export default {
  props: {
    task: Object,
    index: Number
  },
  methods: {
    deleteTask() {
      this.$emit("deleteTask", this.index);
    },
    editTaskName(){
      return this.amEditingTask = true;
    },
    saveTask(task){
      this.taskInstance = task;
      this.amEditingTask = false;
    },
    cancelTask(){
      this.amEditingTask = false;
    }
  },
  data(){
    return{
      amEditingTask: false,
      taskInstance: this.task
    }
  },
  components: {
    ManagerNameEdit
  },
};
</script>

<style scoped>
.ist_checkbox {
  border: 1px solid gray;
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-size: 2px 2px;
  background-repeat: no-repeat;
  background-position: center center;
  transition: background-color 150ms ease-in;
}

.task_item td.checker .ist_checkbox {
  position: relative;
  top: 2px;
}
.task_item.priority_1 .ist_checkbox {
  background-color: transparent;
}
.ist_checkbox {
  user-select: none;
  text-align: center;
  line-height: 16px;
  border: 1px solid gray;
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-size: 2px 2px;
  background-repeat: no-repeat;
  background-position: center center;
  transition: background-color 150ms ease-in;
}
.ist_checkbox svg {
  border: 1px solid transparent;
  display: inline-block;
  opacity: 0;
  transition: opacity 150ms ease-in;
  width: 14px;
  height: 14px;
  margin-top: 1px;
  pointer-events: none;
}
.priority_1 .ist_checkbox {
  width: 16px;
  height: 16px;
}

.ist_checkbox:hover svg {
  opacity: 1;
}
.task_item .checker {
  padding-right: 1em;
}
.task_item {
  margin-top: 20px;
}
.task_item .task_content_item {
  font-size: 14px;
  border-bottom: 1px solid #f0f0f0;
}
td.checker.sel_checkbox_td {
  width: 25px;
}
td.text_cursor.content.task_content_item {
  padding-bottom: 10px;
}
td.text_cursor.content.task_content_item {
  width: 400px;
}
.task_item.priority_1 .ist_checkbox:hover {
  background-color: rgba(128, 128, 128, 0.2);
}
.task_item td.checker .ist_checkbox {
  position: relative;
  top: 2px;
}
.task_item.priority_1 .ist_checkbox {
  color: #343434;
}
.priority_1 .ist_checkbox {
  width: 16px;
  height: 16px;
}
.task_item.priority_1 .ist_checkbox {
  color: #343434;
}
.ist_checkbox {
  cursor: pointer;
  color: #404040;
  user-select: none;
  text-align: center;
  line-height: 16px;
}
.ist_checkbox {
  width: 16px;
  height: 16px;
  cursor: pointer;
  color: #404040;
  user-select: none;
  text-align: center;
  line-height: 16px;
  border: 1px solid gray;
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-size: 2px 2px;
  background-repeat: no-repeat;
  background-position: center center;
  background-color: transparent;
  transition: background-color 150ms ease-in;
}
.task_item td.checker,
.task_item .task_content_item {
  font-size: 14px;
  border-bottom: 1px solid #f0f0f0;
}
.task_item .checker {
  padding-right: 1em;
}
.task_item td {
  padding-top: 10px;
  padding-bottom: 10px;
}
td {
  vertical-align: top;
}
</style>

