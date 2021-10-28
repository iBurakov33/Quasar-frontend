<template>
    <div>
        <h5 class="text-bold">Одобрено заявок</h5>
        <p class="text-primary" style="font-size: 75px" v-bind:alleads="alleads">{{alleads.totalcount}}</p>
        <p class="text-primary" style="font-size: 35px" v-bind:alleads="alleads">{{alleads.totalsum}} млн</p>
    </div>
</template>

<script>
export default {
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