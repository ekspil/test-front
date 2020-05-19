<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >

      <div >
        Client App

      </div>

    </v-app-bar>

    <v-content>
      <Table :type="type" :entities="entities"/>
      <v-btn @click="type = 'sum'">sum</v-btn>
      <v-btn @click="type = 'max'">max</v-btn>
      <v-btn @click="type = 'min'">min</v-btn>
      <v-btn @click="type = 'avg'">avg</v-btn>
    </v-content>

  </v-app>
</template>

<script>
import Table from './components/Table';
import axios from 'axios'

export default {
  name: 'App',

  components: {
    Table,
  },

  data: () => ({
    entities: [],
    type: 'sum'
  }),
  methods: {
    getData: async function(){
      const {data} = await axios.get('http://localhost:3021/api/v1/getAll')
      this.entities = data
    }
  },
  beforeMount(){
    this.getData()
  },
  mounted() {
    setInterval(this.getData, 5000)
  }

};
</script>
