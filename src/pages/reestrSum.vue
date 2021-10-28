<template>
    <div>
        <p class="col text-bold reestr">Добавление в реестры и официальный перечень площадок субсидий</p>
        <div class="row callblock">
            <div class="col text-primary text-bold callnum" v-bind:reestrSum="reestrSum">{{reestrSum.mik_participants}}</div>
            <div class="col text-primary text-bold callnum" v-bind:reestrSum="reestrSum">{{reestrSum.reestr_soc}}</div>
        </div>
        <div class="row callblock">
            <div class="col text-bold calldiv" v-bind:reestrSum="reestrSum">Участники МИК</div>
            <div class="col text-bold calldiv" v-bind:reestrSum="reestrSum">Заявки на вступление в реестр соц.предприятий</div>
        </div>
        <div class="row callblock">
            <div class="col text-primary text-bold callnum"  v-bind:reestrSum="reestrSum">{{reestrSum.list_ploshadki}}</div>
            <div class="col text-primary text-bold callnum" v-bind:reestrSum="reestrSum">{{reestrSum.req_approved}}</div>
        </div>
        <div class="row callblock">
            <div class="col text-bold calldiv"  v-bind:reestrSum="reestrSum">Заявки на добавление в список площадок</div>
            <div class="col text-bold calldiv"  v-bind:reestrSum="reestrSum">Одобрено заявок</div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      reestrSum: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/leads/mik/reestr/sum')
      .then(response => {
        this.reestrSum = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>