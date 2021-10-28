<template>
    <div>
        <div class="row">
            <div class="col text-primary text-bold" style="font-size: 45px" v-bind:callsPerDay="callsPerDay">{{callsPerDay.totalcalls}}</div>
            <div class="col text-primary text-bold" style="font-size: 45px" v-bind:callsPerDay="callsPerDay">{{callsPerDay.totalleads}}</div>
            <div class="col text-primary text-bold" style="font-size: 45px" v-bind:callsPerDay="callsPerDay">{{callsPerDay.totalgreenzone}}</div>
        </div>
        <div class="row">
            <div class="col text-bold" style="font-size: 20px" v-bind:callsPerDay="callsPerDay">Общее количество звонков</div>
            <div class="col text-bold" style="font-size: 20px" v-bind:callsPerDay="callsPerDay">Общее количество лидов</div>
            <div class="col text-bold" style="font-size: 20px" v-bind:callsPerDay="callsPerDay">Передано в зеленую зону</div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      callsPerDay: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/leads/calls/greenzone/day/27.10.2021')
      .then(response => {
        this.callsPerDay = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>