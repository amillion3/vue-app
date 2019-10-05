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
      <!-- Vue requires unique ids for any element in an array -->
      <tr v-for="employee in employees" :key="employee.id">
        <td>{{ employee.name }}</td>
        <td>{{ employee.email }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  // In Vue, the convention is that the filename and import will be in PascalCase, such as EmployeeTable,
  //  but when used in a template, this will translate to kebab-case, <employee-table>
  export default {
    name: "employee-table",
    props: {
      employees: Array, // Incoming props, an array named `employees`
    }
  }
</script>

<style scoped>

</style>