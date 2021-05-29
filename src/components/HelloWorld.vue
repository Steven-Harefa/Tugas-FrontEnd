<template>
  <div>
    <h1>Tugas Frontend</h1>

    <ul>

        <li v-for="i in todo" :key="i.ID_Pekerjaan">{{i.Nama}}
          
        <button @click="Hapus(i.ID_Pekerjaan)">Hapus</button>
        
        </li>

    </ul>

    <input v-model="Teks" name="Nama"/>
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
          
        ],

        Teks : ''

      }

    },

    created: function(){

      axios.get('http://localhost:3000/todo')
        .then((result) => {
          this.todo = result.data
        })

    },

    methods:{
      tambah: function(){
        const Item_Baru = {Nama:this.Teks}
        axios.post('http://localhost:3000/todo', Item_Baru)
        this.todo.push(Item_Baru)
        this.Teks = ""
        location.reload()
      },

      Hapus: function(id){
        axios.delete(`http://localhost:3000/todo/${id}`)
        location.reload()
      }

    }

  }

</script>


