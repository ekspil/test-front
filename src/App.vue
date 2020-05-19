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
  mounted() {
    axios
            .get('https://api.coindesk.com/v1/bpi/currentprice.json')
            .then(response => (this.entities = response));
  }

};
</script>
