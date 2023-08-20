<template>
  <div>
    <form v-on:submit.prevent="handelSubmit">
      <label>Employee Name</label>
      <input
        type="text"
        v-model="employeeFormData.name"
        @focus="clearStatus"
        @keypress="clearStatus"
        :class="{ 'has-error': submitting && invalidName }"
        ref="firstInput"
      />
      <label>Employee Email</label>
      <input
        type="text"
        v-model="employeeFormData.email"
        @focus="clearStatus"
        @keypress="clearStatus"
        :class="{ 'has-error': submitting && invalidEmail }"
      />
      <p v-if="error && submitting" class="error-text">
        please enter all the required fields
      </p>
      <p v-if="success" class="succes-text">Registered successfully</p>
      <button>Add Employee</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "employee-form",
  data() {
    return {
      submitting: false,
      error: false,
      success: false,
      employeeFormData: {
        name: "",
        email: "",
      },
    };
  },
  methods: {
    clearStatus() {
      this.success = false;
      this.error = false;
    },
    handelSubmit() {
      this.submitting = true;

      if (this.invalidName || this.invalidEmail) {
        this.error = true;
        return;
      }

      this.clearStatus();
      this.$emit("add:employeeFormData", this.employeeFormData);
      this.$refs.firstInput.focus();
      this.employeeFormData = {
        name: "",
        email: "",
      };
      this.submitting = false;
      this.success = true;
      this.error = false;
    },
  },
  computed: {
    invalidName() {
      return this.employeeFormData.name === "";
    },
    invalidEmail() {
      return this.employeeFormData.email === "";
    },
  },
};
</script>
<style scoped>
form {
  margin-bottom: 2rem;
}
.has-error {
  border: 1px solid red;
}
.error-text {
  color: red;
}
.succes-text {
  color: green;
}
</style>