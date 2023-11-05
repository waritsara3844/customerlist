<template>
  <q-page class="padding">
    <div class="q-pa-md" style="max-width: 400px">
      <h4>Customer Form</h4>
      <q-form
        @submit="onSubmit"
        @reset="onReset"
        ref="customerForm"
        class="q-gutter-md"
      >
        <q-input
          filled
          v-model="name"
          label="Your name *"
          hint="Name and surname"
          lazy-rules
          :rules="[(val) => (val && val.length > 0) || 'Please type something']"
        />

        <q-input
          filled
          type="number"
          v-model="age"
          label="Your age *"
          hint="Allow only number"
          lazy-rules
          :rules="[
            (val) => (val !== null && val !== '') || 'Please type your age',
            (val) =>
              (val > 0 && val < 80) || 'Please type a real age between 1-80',
          ]"
        />

        <div>
          <q-btn label="ADD" type="submit" color="primary" />
          <q-btn
            label="Reset"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          />
        </div>
      </q-form>
    </div>
    <div>
      <data-table :customers="customers" />
    </div>
  </q-page>
</template>

<script>
import DataTable from "src/components/DataTable.vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  components: { DataTable },
  data() {
    return {
      name: "",
      age: "",
      customers: [],
      nextId: 1,
    };
  },
  methods: {
    onSubmit() {
      const customers = {
        id: this.nextId++,
        name: this.name,
        age: this.age,
      };
      this.customers.push(customers);
      this.$refs.customerForm.reset();
    },
    onReset() {
      this.name = "";
      this.age = "";
    },
  },
});
</script>
