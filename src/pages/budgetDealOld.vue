<template>
    <div class="row section q-mt-lg" style="display:flex">
        <table class="text-primary text-bold">
            <thead>
                <tr>
                    <th>Топ 5</th>
                    <th>Объем средств, млн</th>
                    <th>Количество заявок</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(budget, index) in docPrepared" :key="index">
                    <td>
                        {{budget.pipename}}
                    </td>
                    <td>
                        {{budget.total_budget}}
                    </td>
                    <td>
                        {{budget.amount}}
                    </td>
                </tr>    
            </tbody>
        </table>
    </div>
</template>


<script>
export default {
  data() {
    return {
        docPrepared: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/budget/total')
      .then(response => {
        this.docPrepared = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>
