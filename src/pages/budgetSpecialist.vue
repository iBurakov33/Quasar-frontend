<template>
    <div>
        <h5 class="text-bold">Заявки в Департаменте</h5>
        <p class="text-primary" style="font-size: 75px" v-bind:budgetSpecialist="budgetSpecialist">{{budgetSpecialist.totalcount}}</p>
        <p class="text-primary" style="font-size: 35px" v-bind:budgetSpecialist="budgetSpecialist">{{budgetSpecialist.totalsum}} млн</p>
    </div>
</template>

<script>
export default {
  data() {
    return {
      budgetSpecialist: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/budget/specialist')
      .then(response => {
        this.budgetSpecialist = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>