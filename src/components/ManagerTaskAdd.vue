<template>
  <li class="manager indent_1">
    <form>
      <table width="100%">
        <tbody>
          <tr>
            <td colspan="2" class="form_content">
              <table>
                <tbody>
                  <tr>
                    <td class="text_box_holder">
                      <input
                        tabindex="1"
                        autocomplete="off"
                        class="richtext_editor sel_richtext_editor"
                        v-model.trim="taskName"
                      >
                    </td>
                        <v-menu
          v-model="menu2"
          :close-on-content-click="false"
          :nudge-right="40"
          lazy
          transition="scale-transition"
          offset-y
          full-width
          min-width="290px"
        >
          <template v-slot:activator="{ on }">
            <v-text-field
              v-model="date"
              prepend-icon="event"
              readonly
              v-on="on"
            ></v-text-field>
          </template>
          <v-date-picker v-model="date" @input="menu2 = false"></v-date-picker>
        </v-menu>
                  </tr>
                </tbody>
              </table>
            </td>
          </tr>
        </tbody>
      </table>
      <table class="td_submit_area">
        <tbody>
          <tr>
            <td align="left" class="td_submit">
              <a href="#" class="ist_button ist_button_red submit_btn" @click="addTask">
                <span>Add Task</span>
              </a>
              <a class="cancel" tabindex="4" @click="cancelTask">Cancel</a>
            </td>
          </tr>
        </tbody>
      </table>
    </form>
  </li>
</template>

<script>
import { VDatePicker, VMenu, VTextField } from 'vuetify/lib'

export default {
  data() {
    return {
      taskName: "",
      hasClickedDate: false,
      date: new Date().toISOString().substr(0, 10),
      menu: false,
      modal: false,
      menu2: false
    };
  },
  methods: {
    addTask() {
      const taskObj = {
        name: this.taskName,
        date: this.date
      }
      this.$emit('addTask', taskObj);
      this.taskName = "";
    },
    cancelTask() {
      this.$emit('cancelTask');
      this.taskName = "";
    },
  },
  components: {
    VDatePicker, VMenu, VTextField
  },
};
</script>

<style scoped>
.cancel,
.cancel_link {
  color: #555;
  cursor: pointer;
  font-size: 13px;
  padding: 2px 5px;
  text-decoration: none;
  white-space: nowrap;
}
.ist_button,
.ist_button:visited {
  font-weight: bold;
  font-size: 13px;
  line-height: 17px;
  padding: 6px 12px 7px 12px;
  border-radius: 3px;
  text-decoration: none;
  text-align: center;
}
.ist_button_red:hover,
.ist_button_red:visited:hover {
  border-color: #b0281a;
  background-color: #c53727;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.15);
}
.cancel:hover,
.cancel_link:hover {
  text-decoration: underline;
}
table {
  width: 100%;
  border-collapse: collapse;
}
.text_box_holder {
  border-right: 1px solid #eee;
  border-right-width: 1px;
  border-right-style: solid;
  border-right-color: rgb(238, 238, 238);
  background-color: white !important;
}
.form_content table,
.form_content .input_container {
  width: 100%;
  border: 1px solid #ddd;
  border-top-color: rgb(221, 221, 221);
  border-top-style: solid;
  border-top-width: 1px;
  border-right-color: rgb(221, 221, 221);
  border-right-style: solid;
  border-right-width: 1px;
  border-bottom-color: rgb(221, 221, 221);
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-left-color: rgb(221, 221, 221);
  border-left-style: solid;
  border-left-width: 1px;
  border-image-source: initial;
  border-image-slice: initial;
  border-image-width: initial;
  border-image-outset: initial;
  border-image-repeat: initial;
  border-radius: 3px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border-bottom-right-radius: 3px;
  border-bottom-left-radius: 3px;
  border-collapse: separate !important;
}
.richtext_editor {
  resize: none;
  outline: 0;
}
.due_date_holder {
  cursor: pointer !important;
  width: 110px;
}
.manager {
  width: 596px;
}
.input_due_date {
  font-size: 13px !important;
  border: 0;
  padding: 0;
  margin-right: 4px;
  outline: 0;
}
li.manager .submit_btn {
  margin-right: 5px;
  margin-top: 5px;
}
.ist_button,
.ist_button:visited {
  font-weight: bold;
  font-size: 13px !important;
  line-height: 17px;
  text-decoration: none;
  padding: 6px 12px 7px 12px;
  position: relative;
  display: inline-block;
  text-shadow: 0 1px 0 #fff;
  background: #f3f3f3;
  white-space: nowrap;
  border: solid 1px #ddd;
  background: linear-gradient(linear, 0 40%, 0 70%, from(#f3f3f3), to(#f1f1f1));
  border-radius: 3px !important;
  color: #202020 !important;
  text-decoration: none !important;
  text-align: center;
}
.items table {
  border-collapse: collapse;
  width: 100%;
}
.ist_button_red,
.ist_button_red:visited {
  background: 0;
  background-color: #db4c3f;
  color: #fff !important;
  text-shadow: none;
  border: 1px solid transparent;
}

.richtext_editor {
  user-select: text !important;
  overflow-wrap: break-word;
  word-wrap: break-word;
  word-break: break-word;
  vertical-align: middle;
}
.text_box_holder {
  font-size: 16px;
  font-family: 'Roboto', sans-serif;
    line-height: 1.5;
}
.due_date_holder {
  padding: 10px;
  cursor: pointer;
}
input {
  border: 0;
  width: 100%;
}
.manager {
  margin-top: 20px;
}
.input_due_date{
  cursor: pointer;
}
.v-text-field {
    padding-top: 0;
    margin-top: 0;
}
.v-input{
  height: 40px;
}
</style>
