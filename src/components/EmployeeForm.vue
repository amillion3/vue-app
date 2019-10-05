<template>
  <div id="employee-form">
    <form @submit.prevent="handleSubmit">
      <label>Employee name</label>
      <input
          ref="first"
          :class="{ 'has-error': submitting && invalidName }"
          v-model="employee.name"
          @focus="clearStatus"
          @keypress="clearStatus"
          type="text"
      />
      <label>Employee Email</label>
      <input
          :class="{'has-error': submitting && invalidEmail }"
          v-model="employee.email"
          @focus="clearStatus"
          type="text"
      />
      <p v-if="error && submitting" class="error-message">
        ❗Please fill out all required fields
      </p>
      <p v-if="success" class="success-message">
        ✅ Employee successfully added
      </p>
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
  export default {
    name: "employee-form",
    data () {
      return {
        submitting: false,
        error: false,
        success: false,
        employee: {
          name: '',
          email: '',
        }
      }
    },
    computed: {
      invalidName() {
        return this.employee.name === '';
      },
      invalidEmail() {
        return this.employee.email === '';
      },
    },
    methods: {
      handleSubmit() {
        this.submitting = true;
        this.clearStatus();
        if (this.invalidName || this.invalidEmail) {
          this.error = true;
          return;
        }
        // `$emit` broadcasts a name of an event and data to its parent component
        // create an event called add:employee, and pass this.employee
        this.$emit('add:employee', this.employee);
        this.$refs.first.focus();
        this.error = false;
        this.submitting = false;
        this.success = true;

      },
      clearStatus() {
        this.error = false;
        this.success = false;
      },
    }
  }
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }

  [class*='-message'] {
    font-weight: 500;
  }

  .error-message {
    color: #d33c40;
  }

  .success-message {
    color: #32a95d;
  }
</style>