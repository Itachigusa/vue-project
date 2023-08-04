<script>
export default {
  props: ["value","index"],
  data(){
    return {
      isOpen:false
    }
  },
  methods:{
    setOpenState(isOpen)
    {
      this.isOpen = isOpen;
      
    },
    onClick()
    {
      if(this.isOpen == false)
      {
        this.$emit('card-open', this.value, this.index)
      }
    }
  }
}
</script>

<template>
<div v-if="isOpen == true">
      <button class = "button">{{value}}</button>
</div>
<div v-if="isOpen == false">
      <button class = "button" @click="onClick">-</button>
</div>
</template>

<style scoped>
.button {
  width:100px;
  height:30px;
}
</style>