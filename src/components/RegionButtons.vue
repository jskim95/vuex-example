<template>
  <div>
      <button class="region" v-for="region in regions" :key="region"
          v-bind:class="isSelected(region)"
          @click="changeRegion({region:region})">
          {{region}}
      </button>
  </div>
</template>

<script>
import Constant from '../Constant'
import { mapMutations, mapGetters } from 'vuex'
export default {
  name : "RegionButtons",
  computed : 
  // vuex helper
  // 1. vuex 속성명 동일한 이름으로 선언
  mapGetters([ 'regions', 'currentRegion', ]),

  // 2. vuex 속성명 이름을 바꿔서 선언
  // mapGetters({
  //   re : 'regions',
  //   currentRegion : 'currentRegion',
  // }),


  // vuex 기본
  // {
  //   regions() {
  //     return this.$store.getters.regions;
  //   },
  //   currentRegion() {
  //     return this.$store.getters.currentRegion;
  //   }
  // },
  methods : {
    isSelected(region) {
      if(region ==  this.currentRegion) return { selected : true};
      else return { selected : false }
    },
    ...mapMutations([
      Constant.CHANGE_REGION
    ])
  }
}
</script>

<style scoped>
button.region {
  text-align: center;
  width: 80px;
  margin: 2px;
  border: solid 1px gray;
}
button.selected {
  background-color: purple;
  color: aqua;
}
</style>
