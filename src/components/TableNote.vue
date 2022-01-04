<template>
  <div class="box">
      <table>
  <tr>
    <th>Nom</th>
    <th>Date</th>
    <th>Note</th>
  </tr>
  <tr v-for="item in notes" :key="item.name">
    <td>{{item.name}}</td>
    <td>{{item.date}}</td>
    <td>{{item.note}}</td>
  </tr>
</table>
  </div>
</template>

<script>
export default {
  name: 'FormNote',
  props: ['notes'],
  mounted(){
    this.notes.sort( function ( a, b ) { return b.note - a.note; } );
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .box{
    width: 500px;
  }
  table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
  
</style>
