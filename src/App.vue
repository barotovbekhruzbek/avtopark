<template>
    <div>
      <Header />
      <Table /> 
    </div>
</template>

<script>

import Header from './components/Header.vue';
import Table from './components/Table.vue';
export default {
  components : {
    Header,
    Table
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>