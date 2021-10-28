<template>
    <div class="q-pa-md">
      <q-table
        :rows="docPrepared"
        :columns="columns"
        row-key="pipename"
        :hide-pagination="true"
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
        { name: 'totalcount', 
          align: 'left', 
          label: 'Количество заявок', 
          field: 'totalcount', 
          sortable: true
        }
      ],
      docPrepared: []
    }
  },
  mounted() {
    this.$axios
      .get('https://mec.standsystematic.ru/api/leads/docprepared')
      .then(response => {
        this.docPrepared = response.data
      })
      .catch(error => console.log('Error', error.message))
  }
}
</script>