<template>
  <div>
    <h1>LIST OF NINJAS</h1>
    <ul>
      <li v-for="wrestler in wrestlers">{{wrestler}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      wrestlers: ['stone cold steve austin', 'the rock', 'DX', 'the undertaker', 'mankind']
    }
  }
}
</script>

<style scoped lang="scss">
h1{
  color: green;
}
</style>
