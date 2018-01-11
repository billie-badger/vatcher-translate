<template>
  <h1 class="text-success">{{translatedText}}</h1>
</template>

<script>

export default {
  name: 'translateOutput',
  props:['translatedText']
}
</script>

<style>
  .text-success{
    font-family: 'Arial', sans-serif;
    font-size: 2em;
    color: #65d875;
  }
</style>
