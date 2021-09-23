<template>
  <div class='home'>
        <table-Department :tableParam="departmentsData"></table-Department>
  </div>
</template>

<script>
//import TableDepartmentVue from '../components/TableDepartment.vue';
// @ is an alias to /src
//import Department from '@/components/Department.vue';
import TableDepartment from '@/components/TableDepartment.vue';

export default {
  name: 'Home',
  components: {
    "table-Department": TableDepartment

  },
  created() {
    this.getDepartments();
  },
  data() {
    return {
      departmentsData: []
    };
  },
  methods: {
    async getDepartments() {
      const res = await fetch('http://localhost:9559/api/department');
      const resJson = await res.json();
      //console.log(resJson);
      this.departmentsData = resJson;
    }
  }
}
</script>
