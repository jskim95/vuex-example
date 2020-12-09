<template>
  <div id="example">
    <table id="list">
      <thead>
        <tr>
          <th>번호</th>
          <th>국가명</th>
          <th>수도</th>
          <th>지역</th>
          <th></th>
        </tr>
      </thead>
      <tbody id="contacts">
        <tr v-for="c in countries" :key="c.no">
          <td>{{c.no}}</td>
          <td>{{c.name}}</td>
          <td>{{c.capital}}</td>
          <td>{{c.region}}</td>
          <button @click="deleteRegion(c.no)">삭제</button>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
import Constant from '../Constant'
export default {
  name : 'countryList',
  computed : mapGetters({
    countries : 'countriesByRegion'
  }),
  methods : {
    ...mapActions([Constant.DELETE_REGION])
  }
}
</script>

<style>
#list {
  width: 550px;
  border: 1px solid black;
  border-collapse: collapse;
}
#list td, #list th {
  border:1px solid black;
  text-align: center;
}

#list td:nth-child(5n+1), #list th:nth-child(5n+1) { width: 10px; }
#list td:nth-child(5n+2), #list th:nth-child(5n+2) { width: 150px; }
#list td:nth-child(5n+3), #list th:nth-child(5n+3) { width: 150px; }
#list td:nth-child(5n+4), #list th:nth-child(5n+4) { width: 50px; }
#list td:nth-child(5n), #list th:nth-child(5n) { width: 10px; }
#list > thead > tr {
  color: yellow;
  background-color: purple;
}
</style>
