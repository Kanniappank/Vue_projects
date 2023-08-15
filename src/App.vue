<template>
  <div class="small-container">
    <h1>Employee</h1>
    <employee-form @add:employeeFormData="addEmployee"/>
    <employee-table :employeesData="employeesData"/>
  </div>
</template>

<script>
import EmployeeForm from './components/EmployeeForm.vue';
import EmployeeTable from "./components/EmployeeTable.vue";

export default {
  name: "App",
  components: {
    EmployeeTable,
    EmployeeForm,
  },
  data() {
    return {
      employeesData: [
        { id: 1, name: "Ram", email: "ram@gmail.com" },
        { id: 2, name: "Ranjith", email: "ranjith@gmail.com" },
        { id: 3, name: "Raghu", email: "raghu@gmail.com" },
      ],
    };
  },
  methods:{
    addEmployee(employee){
        this.employeesData=[...this.employeesData,employee]
      }
  }
};
</script>

<style>
button {
  background: green;
  border: 1px solid green;
}
.small-container {
  max-width: 680px;
}
</style>
