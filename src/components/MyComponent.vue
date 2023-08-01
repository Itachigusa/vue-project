<script>
export default {
  props: ["title","body","msg"]
}
</script>

<template>
   <div>
       <h3>{{title}}</h3>
       <p>{{body}}</p>
       <p>{{msg}}</p>
   </div>
</template>

<style scoped>
</style>