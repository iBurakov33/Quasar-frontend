<template>
    <div>
        <h5 class="text-bold">Готовят документы</h5>
        <p class="text-primary" style="font-size: 75px" v-bind:docpreparedTotal="docpreparedTotal">
            {{docpreparedTotal.totalcount}}
        </p>
        <p class="text-primary" style="font-size: 35px" v-bind:docpreparedTotal="docpreparedTotal">
            предпринимателей
        </p>
    </div>
</template>

<script>
export default {
  data() {
    return {
      docpreparedTotal: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/leads/docprepared/total')
      .then(response => {
        this.docpreparedTotal = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>