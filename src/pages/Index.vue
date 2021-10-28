<template>
  <div class="q-pa-md main">
    <h3 class="title text-bold" >Основные показатели<br> о ходе субсидийной кампании</h3>
    <q-separator/>
    <h5 class="text-primary text-bold">Текущий объем средств к выдаче</h5>
    <div class="row section q-mt-lg" style="display:flex">
      <div class="col-12 col-md-4 col-lg-3 line" style="padding: 0px 0px 0px 15px">
        <div class="col q-mt-lg">
         <p><alleads /><q-separator/></p>
        </div>
        <div class="col q-mt-lg">
          <p><alleads-signed /><q-separator/></p>
        </div>
        <div class="col q-mt-lg">
          <p><alleads-given /></p>
        </div>
      </div>
      <q-separator vertical inset />
      <div class="col-12 col-md-8">
       <div class="row" style="display:flex">
          <p class="budget_chart"><budget-all /></p>
        </div>
      </div>
    </div>

    <q-separator />
    <h5 class="text-primary text-bold">Потенциальный объем средств к выдаче</h5>
    <div class="row section q-mt-lg" style="display:flex">
      <div class="col-12 col-md-4 col-lg-3 line q-mr-lg" style="padding: 0px 0px 0px 15px">
        <div class="col q-mt-lg">
          <p><budget-specialist /></p>
        </div>
        <div class="col q-mt-lg block_prepare">
          <p><docprepared-total /></p>
        </div>
      </div>
      <q-separator vertical inset />
      <div class="col-12 col-md-8 col-lg-8 line q-mr-lg">
        <div class="col q-mt-lg">
          <p><budget-deals /></p>
        </div>
        <div class="col q-mt-lg">
          <p><doc-prepared /></p>
        </div>
      </div>
    </div>

    <q-separator />
    <h5 class="text-bold">Работа колл-центра</h5>
    <div class="row section q-mt-lg callmain" style="display:flex">
      <div class="col-12 col-md-6 col-lg-6 line">
        <div class="col q-mt-lg">
         <p><calls-per-day /></p>
        </div>
        <div class="col q-mt-lg">
         <p><calls-total /></p>
        </div>
      </div>
      <div class="col-12 col-md-6 col-lg-6 line bg-secondary">
        <div class="col q-mt-lg">
         <p class="reestr_sum"><reestr-sum /></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import alleadsSigned from './alleadsSigned'
import alleadsGiven from './alleadsGiven.vue'
import alleads from './alleads.vue'
import budgetAll from './budgetAll.vue'
import budgetSpecialist from './budgetSpecialist.vue'
import docpreparedTotal from './docpreparedTotal.vue'
import docPrepared from './docPrepared.vue'
import callsPerDay from './callsPerDay.vue'
import callsTotal from './callsTotal.vue'
import reestrSum from './reestrSum.vue'
import budgetDeals from './budgetDeals.vue'
import  '../css/style.css'

export default {
  components: {
    alleads,
    alleadsSigned,
    alleadsGiven,
    budgetAll,
    budgetSpecialist,
    docpreparedTotal,
    docPrepared,
    callsPerDay,
    callsTotal,
    reestrSum,
    budgetDeals
  },
  data() {
    return {
      alleads: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/budget/alleads')
      .then(response => {
        this.alleads = response.data
      })
      .catch(error => console.log('Error', error.message))  
  }
}
</script>
