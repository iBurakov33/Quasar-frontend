<template>
    <div>
        <h5 class="text-bold">Всего</h5>
        <div class="row">
            <div class="col text-primary text-bold callnum_total"  v-bind:callsTotal="callsTotal">{{callsTotal.totalcalls}}</div>
            <div class="col text-primary text-bold callnum_total"  v-bind:callsTotal="callsTotal">{{callsTotal.totalleads}}</div>
            <div class="col text-primary text-bold callnum_total"  v-bind:callsTotal="callsTotal">{{callsTotal.totalgreenzone}}</div>
        </div>
        <div class="row">
            <div class="col text-bold calldiv"  v-bind:callsTotal="callsTotal">Общее количество звонков</div>
            <div class="col text-bold calldiv"  v-bind:callsTotal="callsTotal">Общее количество лидов</div>
            <div class="col text-bold calldiv"  v-bind:callsTotal="callsTotal">Передано в зеленую зону</div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      callsTotal: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/leads/calls/greenzone')
      .then(response => {
        this.callsTotal = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>