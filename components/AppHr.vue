<template>
  <div><hr /></div>
</template>
<script lang="ts"></script>
<style scoped>
hr {
  padding: 0;
  border: none;
  border-top: medium double #333;
  color: #333;
  text-align: center;
}
hr::after {
  content: '§';
  display: inline-block;
  position: relative;
  top: -0.9em;
  font-size: 1.5em;
  padding: 0 0.25em;
  background: #f4f0e7;
}
</style>
e
