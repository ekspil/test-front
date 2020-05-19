<template>
  <v-data-table
          :headers="headers"
          :items="ent"
          :items-per-page="20"
          :footer-props="footerProps"
          class="elevation-1"
          dense
  >
    <v-data-footer>
      Hello
    </v-data-footer>

    <template v-slot:item.value1="{item}">
      <v-chip :color="getColor(item.value1, item.id)" :text-color="getInvertColor(item.value1, item.id)" >{{ item.value1 }}</v-chip>
    </template>
    <template v-slot:item.value2="{item}">
      <v-chip :color="getColor(item.value2, item.id)" :text-color="getInvertColor(item.value2, item.id)" >{{ item.value2 }}</v-chip>
    </template>
    <template v-slot:item.value3="{item}">
      <v-chip :color="getColor(item.value3, item.id)" :text-color="getInvertColor(item.value3, item.id)" >{{ item.value3 }}</v-chip>
    </template>
    <template v-slot:item.value4="{item}">
      <v-chip :color="getColor(item.value4, item.id)" :text-color="getInvertColor(item.value4, item.id)" >{{ item.value4}}</v-chip>
    </template>
    <template v-slot:item.value5="{item}">
      <v-chip :color="getColor(item.value5, item.id)" :text-color="getInvertColor(item.value5, item.id)" >{{ item.value5 }}</v-chip>
    </template>
    <template v-slot:item.value6="{item}">
      <v-chip :color="getColor(item.value6, item.id)" :text-color="getInvertColor(item.value6, item.id)" >{{ item.value6 }}</v-chip>
    </template>
    <template v-slot:item.value7="{item}">
      <v-chip :color="getColor(item.value7, item.id)" :text-color="getInvertColor(item.value7, item.id)" >{{ item.value7 }}</v-chip>
    </template>
    <template v-slot:item.value8="{item}">
      <v-chip :color="getColor(item.value8, item.id)" :text-color="getInvertColor(item.value8, item.id)" >{{ item.value8 }}</v-chip>
    </template>
    <template v-slot:item.value9="{item}">
      <v-chip :color="getColor(item.value9, item.id)" :text-color="getInvertColor(item.value9, item.id)" >{{ item.value9 }}</v-chip>
    </template>
    <template v-slot:item.value10="{item}">
      <v-chip :color="getColor(item.value10, item.id)" :text-color="getInvertColor(item.value10, item.id)" >{{ item.value10 }}</v-chip>
    </template>
    <template v-slot:item.value11="{item}">
      <v-chip :color="getColor(item.value11, item.id)" :text-color="getInvertColor(item.value11, item.id)" >{{ item.value11 }}</v-chip>
    </template>
    <template v-slot:item.value12="{item}">
      <v-chip :color="getColor(item.value12, item.id)" :text-color="getInvertColor(item.value12, item.id)" >{{ item.value12 }}</v-chip>
    </template>
    <template v-slot:item.value13="{item}">
      <v-chip :color="getColor(item.value13, item.id)" :text-color="getInvertColor(item.value13, item.id)" >{{ item.value13 }}</v-chip>
    </template>
    <template v-slot:item.value14="{item}">
      <v-chip :color="getColor(item.value14, item.id)" :text-color="getInvertColor(item.value14, item.id)" >{{ item.value14 }}</v-chip>
    </template>
    <template v-slot:item.value15="{item}">
      <v-chip :color="getColor(item.value15, item.id)" :text-color="getInvertColor(item.value15, item.id)" >{{ item.value15 }}</v-chip>
    </template>
    <template v-slot:item.value16="{item}">
      <v-chip :color="getColor(item.value16, item.id)" :text-color="getInvertColor(item.value16, item.id)" >{{ item.value16 }}</v-chip>
    </template>
    <template v-slot:item.value17="{item}">
      <v-chip :color="getColor(item.value17, item.id)" :text-color="getInvertColor(item.value17, item.id)" >{{ item.value17 }}</v-chip>
    </template>
    <template v-slot:item.value18="{item}">
      <v-chip :color="getColor(item.value18, item.id)" :text-color="getInvertColor(item.value18, item.id)" >{{ item.value18 }}</v-chip>
    </template>
    <template v-slot:item.value19="{item}">
      <v-chip :color="getColor(item.value19, item.id)" :text-color="getInvertColor(item.value19, item.id)" >{{ item.value19 }}</v-chip>
    </template>
    <template v-slot:item.value20="{item}">
      <v-chip :color="getColor(item.value20, item.id)" :text-color="getInvertColor(item.value20, item.id)" >{{ item.value20 }}</v-chip>
    </template>
  </v-data-table>
</template>

<script>
  export default {
    name: 'Table',
    props: {

      type: {
        type: String,
        default: "sum"
      },
      entities: {
        type: Array,
        default: () => []
      }
    },
    methods: {
      getColor(value, id){
        if(id === "Итого") return "white"
        if(value === 0) return "rgb(255,255,255)"
        if(value > 0 && value < 1) return `rgba(0, 0, 0, ${Math.abs(value)})`
        if(value >= -1 && value < 0) return `rgba(255, 140, 0, ${Math.abs(value)})`
        if(value === 1) return "rgb(0,0,0)"
      },
      getInvertColor(value, id){
        if(id === "Итого") return "black"
        if(Math.abs(value) < 0.5) return `rgb(0, 0, 0)`
        if(Math.abs(value) > 0.5) return `rgb(255, 255, 255)`
      },
    },
    computed: {
      summ: function () {
          return this.entities.reduce((acc, item) => {
            for (let value in item){
                if (value.includes("value")) {
                  acc[value] += item[value]
                }

            }

            for (let i in acc){
              if(i.includes("value")){
                acc[i] = Number(acc[i].toFixed(2))
              }

            }
            return acc
          }, JSON.parse(JSON.stringify(this.temp)))
      },
      max: function () {
          return this.entities.reduce((acc, item) => {
            for (let value in item){
                if (value.includes("value")) {
                  acc[value] = Math.max(item[value], acc[value])
                }

            }

            for (let i in acc){
              if(i.includes("value")){
                acc[i] = Number(acc[i].toFixed(2))
              }

            }
            return acc
          }, JSON.parse(JSON.stringify(this.temp)))
      },
      min: function () {
          return this.entities.reduce((acc, item) => {
            for (let value in item){
                if (value.includes("value")) {
                  acc[value] = Math.min(item[value], acc[value])
                }

            }

            for (let i in acc){
              if(i.includes("value")){
                acc[i] = Number(acc[i].toFixed(2))
              }

            }
            return acc
          }, JSON.parse(JSON.stringify(this.temp)))
      },
      avg: function() {
        const obj = JSON.parse(JSON.stringify(this.temp))
        for (let value in this.summ){
          if (value.includes("value")) {
            obj[value] = this.summ[value] / this.entities.length
          }


        }
        return obj
      },
      ent: function () {
          if(this.type === "sum") return [...this.entities, this.summ]
          if(this.type === "max") return [...this.entities, this.max]
          if(this.type === "min") return [...this.entities, this.min]
          if(this.type === "avg") return [...this.entities, this.avg]
          else return []
      }

    },
    data: () => ({
      footerProps: {
        disableItemsPerPage: true,
        itemsPerPageOptions: [20]
      },
      headers: [
        {
          text: 'Entity ID',
          align: 'start',
          sortable: true,
          value: 'id',
        },
        { text: 'Value1', value: 'value1' },
        { text: 'Value2', value: 'value2' },
        { text: 'Value3', value: 'value3' },
        { text: 'Value4', value: 'value4' },
        { text: 'Value5', value: 'value5' },
        { text: 'Value6', value: 'value6' },
        { text: 'Value7', value: 'value7' },
        { text: 'Value8', value: 'value8' },
        { text: 'Value9', value: 'value9' },
        { text: 'Value10', value: 'value10' },
        { text: 'Value11', value: 'value11' },
        { text: 'Value12', value: 'value12' },
        { text: 'Value13', value: 'value13' },
        { text: 'Value14', value: 'value14' },
        { text: 'Value15', value: 'value15' },
        { text: 'Value16', value: 'value16' },
        { text: 'Value17', value: 'value17' },
        { text: 'Value18', value: 'value18' },
        { text: 'Value19', value: 'value19' },
        { text: 'Value20', value: 'value20' },
      ],
      temp: {id: "Итого",
        value1: 0,
        value2: 0,
        value3: 0,
        value4: 0,
        value5: 0,
        value6: 0,
        value7: 0,
        value8: 0,
        value9: 0,
        value10: 0,
        value11: 0,
        value12: 0,
        value13: 0,
        value14: 0,
        value15: 0,
        value16: 0,
        value17: 0,
        value18: 0,
        value19: 0,
        value20: 0,},

    }),
  }
</script>
