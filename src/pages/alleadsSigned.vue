<template>
    <div>
        <h5 class=" text-bold">Заключено соглашений</h5>
        <p class="text-primary" style="font-size: 75px" v-bind:alleadsSigned="alleadsSigned">{{alleadsSigned.totalcount}}</p>
        <p class="text-primary" style="font-size: 35px" v-bind:alleadsSigned="alleadsSigned">{{alleadsSigned.totalsum}} млн</p>
    </div>
</template>

<script>
export default {
  data() {
    return {
      alleadsSigned: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/budget/alleads/signed')
      .then(response => {
        this.alleadsSigned = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>