<template>
  <div id="app">
    <v-app>
     <editor></editor>
    </v-app>
  </div>
</template>

<script>
import Editor from "./components/Editor.vue";

export default {
  name: "app",
  components: {
    Editor
  }
};
</script>
