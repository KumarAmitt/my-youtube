<template>
  <div>
    <input @input="onInput" placeholder="Search"/>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(e){
      this.$emit('termChange', e.target.value);
    }
  }
}
</script>

<style scoped>
input {
  width: 75%;
}

div {
  text-align: center;
  margin: 20px;
}
</style>
