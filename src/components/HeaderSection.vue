<template>
  <h2 class="section_header">
    Today
    <span class="subsection_header__date">{{date}}</span>
  </h2>
</template>

<script>
export default {
  computed: {
    date() {
      var objToday = new Date(),
        weekday = new Array(
          "Sunday",
          "Monday",
          "Tuesday",
          "Wednesday",
          "Thursday",
          "Friday",
          "Saturday"
        ),
        dayOfWeek = weekday[objToday.getDay()],
        domEnder = (function() {
          var a = objToday;
          if (/1/.test(parseInt((a + "").charAt(0)))) return "th";
          a = parseInt((a + "").charAt(1));
          return 1 == a ? "st" : 2 == a ? "nd" : 3 == a ? "rd" : "th";
        })(),
        dayOfMonth =
          today + (objToday.getDate() < 10)
            ? "0" + objToday.getDate()
            : objToday.getDate(),
        months = new Array(
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December"
        ),
        curMonth = months[objToday.getMonth()],
        curYear = objToday.getFullYear(),
        curHour =
          objToday.getHours() > 12
            ? objToday.getHours() - 12
            : objToday.getHours() < 10
            ? "0" + objToday.getHours()
            : objToday.getHours(),
        curMinute =
          objToday.getMinutes() < 10
            ? "0" + objToday.getMinutes()
            : objToday.getMinutes(),
        curSeconds =
          objToday.getSeconds() < 10
            ? "0" + objToday.getSeconds()
            : objToday.getSeconds(),
        curMeridiem = objToday.getHours() > 12 ? "PM" : "AM";
      var today = dayOfWeek + ", " + curMonth + " " + dayOfMonth;

      return today;
    }
  }
};
</script>


<style scoped>
.subsection_header__date {
  color: #808080 !important;
  margin-left: 6px;
  font-size: 11px;
  font-weight: normal;
}
.section_header,
.project_link {
  color: #333;
  text-decoration: none !important;
}
.section_header {
  font-size: 20px !important;
  font-weight: normal;
}
</style>
