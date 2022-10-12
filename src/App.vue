<template>
  <div id="app">
    <pagination-list :list-array="pageArray" />
    <pagination-numbers :total-rows="total" @clicked="paginateItems" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import PaginationList from "./components/PaginationList.vue";
import PaginationNumbers from "./components/PaginationNumbers.vue";
import axios from "axios";

@Component({
  components: {
    PaginationList,
    PaginationNumbers,
  },
})
export default class App extends Vue {
  public pageArray: any = [];
  public total = 0;
  public paginatedItems = [];
  public perPage = 12;

  public created() {
    axios
      .get("http://sample.bmaster.kro.kr/contacts")
      .then((response: any) => {
        const contacts = response.data.contacts;
        this.pageArray = contacts;
        this.total = contacts.length;
      })
      .catch((err) => {
        console.log(err);
      });
  }

  public paginateItems(current_Page: any, perPage: any) {
    console.log("current_Page: ", current_Page);
    console.log("perPage: ", this.perPage);
    // const itemsToParse = this.pageArray;
  }

  // 첫 마운트 시
  public mounted(): void {
    // this.paginateItems();
  }

  // paginated 순서
  // 첫 mount시 보여줄 데이터 구현
  // 버튼 눌렀을 때 보여줄 데이터 구현
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
