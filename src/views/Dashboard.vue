<template>
  <v-container>
    <div>
      <h1>Dashboard</h1>
      <v-row>
        <v-col v-for="sale in salesData" :key="`${sale.title}`" cols="12" md="4">
          <SalesGraph :sale="sale.stats" />
        </v-col>
      </v-row>
      <v-row>
        <v-col v-for="item in statisticsData" :key="`${item.label}`" cols="12" sm="6" md="3">
          <StatisticCard :item="item" />
        </v-col>
      </v-row>
      <v-row id="below-the-fold" v-intersect="showMoreContent">
        <v-col cols="12" sm="8">
          <DessertsTable :headers="dessertsData.headers" :desserts="dessertsData.desserts" />    
        </v-col>
        <v-col cols="12" sm="4">
          <EventTimeLine :items="timeline" />
        </v-col>
      </v-row>
      <v-row v-if="loadNewContent" id="more-content">
        <v-col>
          <v-skeleton-loader
            ref="skeleton"
            type="table"
            class="mx-auto"
          ></v-skeleton-loader>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script>
import StatisticCard from '../components/StatisticCard'
import EventTimeLine from '../components/EventTimeLine'
import SalesGraph from '../components/SalesGraph'
import DessertsTable from '../components/DessertsTable'

import dessertsData from '../data/desserts.json'
import statisticsData from '../data/statistics.json'
import timeline from '../data/timeline.json'
import salesData from '../data/sales.json'

export default {
  components: {
    StatisticCard,
    EventTimeLine,
    SalesGraph,
    DessertsTable
  },
  data () {
    return {
      loadNewContent: false,
      dessertsData,
      statisticsData,
      timeline,
      salesData
    }
  },  
  methods: {
    showMoreContent (entries) {
      this.loadNewContent = entries[0].isIntersecting // skeleton only loads if user scrolls down past certain point
    }
  }
};
</script>

<style>
</style>