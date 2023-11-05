<template>
  <div class="q-pa-md">
    <q-table
      title="Customer Details"
      :rows="customers"
      :columns="columns"
      row-key="id"
    />
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "DataTable",
  props: {
    customers: {
      type: Array,
    },
  },
  data() {
    return {
      columns: [
        {
          name: "id",
          required: true,
          label: "ID",
          align: "left",
          field: "id",
          sortable: true,
        },
        {
          name: "name",
          required: true,
          label: "name",
          align: "left",
          field: "name",
          sortable: true,
        },
        {
          name: "age",
          required: true,
          label: "Age",
          align: "left",
          field: "age",
          sortable: true,
        },
      ],
    };
  },
});
</script>
