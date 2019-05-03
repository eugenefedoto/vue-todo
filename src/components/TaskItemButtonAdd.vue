<template>
  <li class="agenda_add_task">
    <a href="#" class="action">
      <span class="icon icon_add">
        <svg
          width="13"
          height="13"
          viewBox="0 0 13 13"
          xmlns="http://www.w3.org/2000/svg"
          data-svgs-path="sm1/plus.svg"
        >
          <path
            d="M6 6V.5a.5.5 0 0 1 1 0V6h5.5a.5.5 0 1 1 0 1H7v5.5a.5.5 0 1 1-1 0V7H.5a.5.5 0 0 1 0-1H6z"
            fill="currentColor"
            fill-rule="evenodd"
          ></path>
        </svg>
      </span>Add Task
    </a>
  </li>
</template>

<style scoped>
.icon_add {
  color: #dd4b39;
  cursor: pointer;
}
.agenda_add_task:hover .action .icon_add {
  color: #fff;
  background-color: #dd4b39;
}
.agenda_add_task .action .icon_add {
  align-items: center;
  border-radius: 50%;
  color: #dd4b39;
  display: inline-flex;
  height: 17px;
  justify-content: center;
  margin-right: 13px;
  transform: translateY(8px);
  vertical-align: 7px;
  width: 17px;
}
.agenda_add_task:hover .action {
  color: #dd4b39 !important;
  text-decoration: none;
}
.agenda_add_task:hover .action .icon_add {
  color: #fff;
  background-color: #dd4b39;
}
.agenda_add_task .action {
    color: #808080 !important;
    padding-right: 1em;
}
a.action {
    cursor: pointer;
    padding: 1px;
    text-decoration: none;
    color: #dd4b39;
    font-size: 14px;
}
.agenda_add_task {
  margin-top: 10px;
}
</style>
