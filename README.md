# vuex-example

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```
<br>

## 참고할 사이트
- https://kdydesign.github.io/2019/04/06/vuejs-vuex-helper/ (여러 store가 있을때 컴포넌트에서 vuex속성 바인딩하는법)
- https://vuex.vuejs.org/kr/guide/state.html (vuex 공식문서)
- https://rnwns2.tistory.com/88?category=391381 (vuex 개념정리)

# vuex 기본
### 준비물  
1. (main.js) : store 등록
2. (store/index.js) : 특정 컴포넌트들에게 공유할 데이터 작성(state, mutations, actions, getters)
3. (특정 컴퓨넌트들) : index.js에서 작성한 기능들 알맞게 사용하기

## 1. main.js
``` javascript
// main.js에서 store를 등록하면 컴포넌트에서 this.$store.속성명 <- 으로 접근이 가능하다

import Vue from 'vue'
import App from './App.vue'
import router from './router'
import store from './store' // store import



new Vue({
  store, // store 등록
  router,
  el: '#app',
  render: h => h(App)
})
```

## 2. src/index.js
``` javascript
// vuex store구조

import Vue from 'vue';
import Vuex from 'vuex';

Vue.use(Vuex);

export default new Vuex.Store({

  //vue의 data와 비슷
  state: {
    ...
  },
  
  // 변경된 데이터 업데이트 vue의 computed와 비슷
  getters: {
	...
  },
  
  // state를 수정할 때 사용(동기적)
  mutations:{
    ...
  },
  
  // methods 역할(비동기적)
  actions: {
	...
  },
  
})
```
## 3. src/components/특정컴포넌트
``` javascript
<script>
import mainTitle from './main/mainTitle'
import nowWeather from './weather/nowWeather'

import store from './store'
export default {
  name: 'main',
  store,

  components:{
    'mainTitle': mainTitle,
    'nowWeather': nowWeather,
  },

  computed:{
  	// state
    nowTemperature() {
      return this.$store.state.nowTemperature
    },
    
    // ... 생략
    
    // getters
    test() {
      return this.$store.getters.test
    },
  },
  methods: {
    getData () {
      // actions
      this.$store.dispatch('액션명', payload) // payload 생략 가능
      
      // mutations
      this.$store commit('변이명', payload) // payload 생략 가능
  },
}
</script>
```

# vuex helper 
1. 컴포넌트에서 사용할 vuex속성명 import 하기
2. 사용할 vuex속성 선언하기
``` javascript
<script>
import Constant from '../Constant'
import { mapMutations, mapGetters } from 'vuex'
export default {
  name : "RegionButtons",
  computed : 
  // vuex helper
  // 1. vuex 속성명 동일한 이름으로 바인딩
  mapGetters([ 'regions', 'currentRegion', ]), // 1번째 방법

  // 2. vuex 속성명 이름을 바꿔서 바인딩
  // mapGetters({
  //   re : 'regions',
  //   currentRegion : 'currentRegion', // 2번째 방법
  // }),

  methods : {
    ...mapMutations([ // 3번째 방법
      Constant.CHANGE_REGION
    ])
  }
}
</script>
```