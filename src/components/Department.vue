<template>
  <div>
        <tr>
    <th>        <span style="color:red"> 
        {{ departmentsParam.id }}
        </span></th>
    <th>
        <span style="color:black"> 
        {{departmentsParam.Name }} 
        </span></th>
  </tr>

        
  </div>
</template>

<script>
export default {
  props: ['departmentsParam']
}
</script>
<style lang="">
</style>
