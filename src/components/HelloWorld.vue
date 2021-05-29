<template>
  <div>
    <h1>Tugas Frontend</h1>

    <ul>

        <li v-for="i in todo">{{i.desc}}</li>

    </ul>

    <input v-model="Teks"/>
    <br>
    <br>
    <button @click="tambah">Simpan Data</button>
  </div>
</template>

<script>

  import axios from 'axios'
  
  export default {

    data: function(){

      return {
        todo: [
          // {desc : 'Argus'},
          // {desc : 'Alucard'},
          // {desc : 'Bane'}
        ],

        Teks : ''

      }

    },

    created: function(){

      axios.get('http://localhost:3000/Input')
        .then((result) => {
          this.todo = result.data
        })

    },

    methods:{
      tambah: function(){
        this.todo.push({desc : this.Teks })
      }
    }

  }

</script>


