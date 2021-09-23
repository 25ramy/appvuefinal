<template>
  <div>
      <p>table: </p>
<b-table ref="table" :items="items" :fields="fields">
   </b-table>
        
  </div>
</template>

<script>
export default {
  props: ['tableParam'],
  watch:{tableParam: function(){this.buildDepartments()}},
    mounted () {
    this.buildDepartments();
  },
    data() {
    return {
      items: [],
      fields: ['id', 'Name']
    };},
     methods: {
    buildDepartments() {
    console.log(this.$props);
      this.items=this.$props.tableParam 
        .map(department => {
          return {
            id: department.id,
            Name: department.Name,
          }
        })
        }
     }
}
</script>
<style lang="">
</style>
