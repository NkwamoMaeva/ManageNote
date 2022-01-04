<template>
  <div class="box">
    <TableNote class="table_section" :notes="notes"/>
    <div class="form_section">
      <div class="item">
        <span>Nom</span>
        <input type="text" v-model="name">
      </div>
      <div class="item">
        <span>Date</span>
        <input type="date" v-model="date">
      </div>
      <div class="item">
        <span>Note</span>
        <input type="number" v-model="note" step="0.1">
      </div>
      <button @click="addNote">Ajouter</button>
    </div>
  </div>
  
</template>

<script>
import TableNote from './TableNote.vue'

export default {
  name: 'FormNote',
  components: {
    TableNote
  },
  data: () =>{
    return{
      name:'',
      date:'',
      note: 0,
      newItem: null,
      notes: JSON.parse(localStorage.getItem('notes'))
    }
  },
  methods: {
    addNote() {
      if(this.name !== '' && this.name !== '' ){
        this.newItem= {
            name: this.name,
            date: this.date,
            note: this.note
          }
      
        this.notes.push(this.newItem);
        this.saveNotes();
      }
    },
    saveNotes() {
      this.notes.sort( function ( a, b ) { return b.note - a.note; } );
      let parsed = JSON.stringify(this.notes);
      localStorage.setItem('notes', parsed);
      this.newItem={}
      this.name=''
      this.date=''
      this.note=0
      location.reload()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .table_section{
    margin-right: 50px;
  }
  .box{
    display: flex;
    justify-content: center;
  }
  .form_section{
    display: flex;
    flex-direction: column;
    width: 500px;
  }
  .item{
    margin-bottom: 20px;
  }
  span{
    width: 50px;
    margin-right: 10px;
  }
  input{
    width: 300px;
    height: 28px;
    border-radius: 5px;
    border: grey 2px solid;
  }
  button{
    margin-top: 25px;
    width: 300px;
    height: 28px;
    background-color: white;
    border-radius: 5px;
    border: grey 2px solid;
    color: #131212;
    cursor: pointer;
  }
</style>
