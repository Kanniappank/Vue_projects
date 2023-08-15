<template>
  <div>
    <form v-on:submit.prevent="handelSubmit">
      <label>Employee Name</label>
      <input type="text" v-model="employeeFormData.nameame"/>
      <label>Employee Email</label>
      <input type="text" v-model="employeeFormData.email"/>
      <button>Add Employee</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "employee-form",
  data(){
    return{
        employee:{
            name:'',
            email:''
        }
    }
  },
  methods:{
    handelSubmit(){
        this.$emit('add:employeeFormData',this.employeeFormDemployeeemployeeata)

    }
  }
};
</script>
<style scoped>
form {
  margin-bottom: 2rem;
}
</style>