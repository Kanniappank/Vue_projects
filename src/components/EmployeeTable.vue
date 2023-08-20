<template>
  <div id="employee-table">
    <p v-if="employeesData.length < 1">No Employees</p>
    <table v-else>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employeesData" :key="employee.id">
          <td v-if="editing == employee.id">
            <input type="text" v-model="employee.name" />
          </td>
          <td v-else>{{ employee.name }}</td>
          <td v-if="editing == employee.id">
            <input type="text" v-model="employee.email" />
          </td>
          <td v-else>{{ employee.email }}</td>
          <td v-if="editing == employee.id">
            <button @click="editEmployee(employee)">Save</button>
            <button @click="editing=null">Cancel</button>
          </td>
          <td v-else>
            <button @click="editMode(employee)">Edit</button>
            <button
              class="actions"
              @click="$emit('delete:employee', employee.id)"
            >
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  name: "employee-table",
  props: {
    employeesData: Array,
  },
  data() {
    return {
      editing: null,
    };
  },
  methods: {
    editMode(employee) {
      this.editing = employee.id;
    },
    editEmployee(employee){
      if(employee.name == '' || employee.email == ''){
        return;
      }

      this.$emit("edit:employee",employee.id,employee) //to register that we can pass one or more data to event
      this.editing = null;
    }
    
  },
};
</script>
<style scoped>
.actions {
  margin-left: 5px;
}
</style>