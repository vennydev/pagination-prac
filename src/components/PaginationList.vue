<template>
  <div>
    <b-table-simple hover small resoponsive>
      <b-thead head-variant="light">
        <b-tr>
          <b-th>NO</b-th>
          <b-th>TEL</b-th>
          <b-th>ADDRESS</b-th>
          <b-th>NAME</b-th>
        </b-tr>
      </b-thead>
      <b-tbody>
        <b-tr v-for="list in listArray" :key="list.no">
          <b-th>{{ list.no }}</b-th>
          <b-th>{{ list.tel }}</b-th>
          <b-th>{{ list.address }}</b-th>
          <b-th>{{ list.name }}</b-th>
        </b-tr>
      </b-tbody>
    </b-table-simple>
  </div>
</template>

<script>
export default {
  props: {
    listArray: {
      type: Array,
      required: true,
    },
  },
  created() {
    console.log("pageArray: ", this.listArray);
  },
};
</script>

<style lang="scss" scoped></style>
