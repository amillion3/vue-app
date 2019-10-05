<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>

    <!-- Passing 'employees' as a prop... -->
    <employee-table v-bind:employees="employees"/>
  </div>
</template>

<script>
  // Using the '@', specifies the `src` directory
  import EmployeeTable from '@/components/EmployeeTable.vue'

  export default {
    name: 'app',
    components: {
      EmployeeTable,
    },
    data() {
      return {
        employees: [
          {
            id: 1,
            name: 'Ben Smith',
            email: 'bsmith@gmail.com',
          },
          {
            id: 2,
            name: 'Steve Brennon',
            email: 'sbrennon@gmail.com',
          },
          {
            id: 3,
            name: 'Richard Sully',
            email: 'rsully@gmail.com',
          },
        ],
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  button {
    background: #009435;
    border: 1px solid #009435;
  }

  .small-container {
    max-width: 680px;
  }

</style>
