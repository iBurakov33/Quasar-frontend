<template>
    <div class="q-pa-md">
      <q-table
        :rows="docPrepared"
        :columns="columns"
        row-key="pipename"
        :hide-pagination = "true"
        :binary-state-sort = "true"
        :column-sort-order="da"
      >
        <template v-slot:header="props">
          <q-tr :props="props">
            <q-th
              v-for="col in props.cols"
              :key="col.name"
              :props="props"
              class="bg-primary text-white"
            >
              {{ col.label }}
            </q-th>
          </q-tr>
        </template>
      </q-table>
    </div>
</template>

<script>
import { api } from 'boot/axios'

export default {
  data() {
    return {
        columns: [
          { name: 'pipename', 
            required: true, 
            label: 'Топ 5', 
            align: 'left', 
            field: 'pipename'
          },
          { name: 'total_budget', 
            align: 'left', 
            label: 'Объем средств, млн', 
            field: 'total_budget', 
            format: val => (val/1000000).toFixed(2)
          },
          { name: 'amount', 
            align: 'left', 
            label: 'Количество заявок', 
            field: 'amount', 
            sortable: true
          }
        ],
        docPrepared: []
    }
  },
  mounted() {
      api.get('https://mec.standsystematic.ru/api/budget/total')
      .then(response => {
        this.docPrepared = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>
