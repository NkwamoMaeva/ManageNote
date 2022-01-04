<template>
  <div id="app">
    <PieChart style="margin: 50px" :notes="notes"/>
    <FormNote/>
  </div>
</template>

<script>
import FormNote from './components/FormNote.vue'
import PieChart from './components/PieChart.vue'

export default {
  name: 'App',
  components: {
    FormNote,
    PieChart
  },
  data: () =>{
    return{
      notes: JSON.parse(localStorage.getItem('notes'))
    }
  },
}
</script>

<style>
#app{
  margin: 0 auto;
}
</style>
