<template>
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employeesData" :key="employee.id">
          <td>{{employee.name}}</td>
          <td>{{employee.email}}</td>
        </tr> 
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  name: "employee-table",
  props:{
    employeesData:Array
  }
};
</script>
<style scoped>
</style>