<template>
  <div class="small-container">
    <h1>Employee</h1>
    <employee-form @add:employeeFormData="addEmployee" />
    <employee-table
      @delete:employee="deleteEmployee"
      @edit:employee="EditEmployee"
      :employeesData="employeesData" 
    />
  </div>
</template>

<script>
import EmployeeForm from "./components/EmployeeForm.vue";
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
  methods: {
    addEmployee(employeeFormData) {
      employeeFormData.id = this.employeesData.length
        ? this.employeesData.length + 1
        : 0;
      this.employeesData = [...this.employeesData, employeeFormData];
    },
    deleteEmployee(id) {
      this.employeesData = this.employeesData.filter((item) => item.id != id);
    },
    EditEmployee(id,updatingEmployee){
      this.employeesData.map(item=> item.id==id?updatingEmployee:item)
    }
  },
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
