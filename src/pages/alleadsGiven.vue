<template>
    <div>
        <h5 class=" text-bold">Получили средства на счет</h5>
        <p class="text-primary" style="font-size: 75px" v-bind:alleadsGiven="alleadsGiven">{{alleadsGiven.totalcount}}</p>
        <p class="text-primary" style="font-size: 35px" v-bind:alleadsGiven="alleadsGiven">{{alleadsGiven.totalsum}} млн</p>
    </div>
</template>

<script>
export default {
  data() {
    return {
      alleadsGiven: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/budget/alleads/given')
      .then(response => {
        this.alleadsGiven = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>