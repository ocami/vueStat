<template>
  <b-row align-h="around">
    <b-col>
      <b-button-group size="lg">
        <b-button :class="{ active: week }" variant="outline-primary" @click="weekSearch">Semaine</b-button>
        <b-button :class="{ active: month }" variant="outline-primary" @click="monthSearch">Mois</b-button>
      </b-button-group>
    </b-col>
    <b-col v-if="month">
      <b-dropdown split split-href="#foo/bar" :text="periodToString" class="m-2">
        <b-dropdown-item  @click="periodSearch('En cours')">En cours</b-dropdown-item>
        <b-dropdown-item  @click="periodSearch('Précédent')">Précédent</b-dropdown-item>
        <b-dropdown-item @click="monthListVisible = true">+</b-dropdown-item>
        <b-dropdown-item v-if="monthListVisible" v-for="(period, key) in periodMonthList" :key="key" @click="periodSearch(period.value)">{{period.toString}}</b-dropdown-item>
      </b-dropdown>
    </b-col>
    <b-col v-if="week">
      <b-dropdown split :text="periodToString" class="m-2">
        <b-dropdown-item v-for="(period, key) in periodWeekList" :key="key" @click="periodSearch(period.value)">{{period.toString}}</b-dropdown-item>
      </b-dropdown>
    </b-col>
    <b-col v-if="monthListVisible">
      <b-dropdown split :text="yearSearch" class="m-2">
        <b-dropdown-item  @click="yearSelect('2019')">2019</b-dropdown-item>
        <b-dropdown-item  @click="yearSelect('2018')">2018</b-dropdown-item>
        <b-dropdown-item  @click="yearSelect('2017')">2017</b-dropdown-item>
      </b-dropdown>
    </b-col>



  </b-row>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      week: false,
      month: true,
      monthListVisible : false,
      period: 'current',
      periodToString: 'En cours',
      yearSearch: '2019',
      periodWeekList : [
        {toString: "En cours", value: "En cours", condition: "current"},
        {toString: "Précédente", value: "Précédente", condition: "last"},
        {toString: "Du 18 au 24 fev", value: "Du 18 au 24 fev", condition: null},
        {toString: "Du 11 au 17 fev", value: "Du 11 au 17 fev", condition: null},
        {toString: "Du 4 au 10 fev", value: "Du 4 au 10 fev", condition: null},
      ],
      periodMonthList : [
        {toString: "Janvier", value: "Janvier", condition: null},
        {toString: "Février", value: "Février", condition: null},
        {toString: "Mars", value: "Mars", condition: null},
        {toString: "Avril", value: "Avril", condition: null},
        {toString: "Mai", value: "Mai", condition: null},
        {toString: "Juin", value: "Juin", condition: null},
        {toString: "Juillet", value: "Juillet", condition: null},
        {toString: "Aout", value: "Aout", condition: null},
        {toString: "Septembre", value: "Septembre", condition: null},
        {toString: "Octobre", value: "Octobre", condition: null},
        {toString: "Novembre", value: "Novembre", condition: null},
        {toString: "Décembre", value: "Décembre", condition: null},
      ]
    }
  },
  computed: {
    // periodToString () {
    //   switch (this.period) {
    //     case 'current':
    //       return 'En cours'
    //     case 'last':
    //       if(this.week) { return 'Précédente' }
    //       if(this.month) { return 'Précédent' }
    //       break; 
    //     default:
    //       console.log('Error : Bilan.vue/computed/periodToString ');
    //       return 'null';
    //   }
    // }
  },
  props: {
    msg: String
  },
  methods: {
    weekSearch: function () {
      console.log('> Bilan/weekSearch')
      this.month = false
      this.week = true
      this.monthListVisible = false
      this.periodToString = 'En cours'
    },
    monthSearch: function () {
      console.log('> Bilan/monthSearch')
      this.month = true
      this.week = false
      this.periodToString = 'En cours'
    },
    periodSearch: function (value) {
      console.log('> Bilan/periodSearch', value)
      this.periodToString = value
      if (value === "En cours" || value === "Précédent") { this.monthListVisible = false }
    },
    yearSelect: function (value) {
      console.log('> Bilan/periodSearch', value)
      this.yearSearch = value
    }
  }    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
