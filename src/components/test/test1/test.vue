<template>
  <div>
    <img :src='pic'>  
  </div>
</template>

<script>
// @ : src(루트)부터 시작
// ../ : 상위 폴더로 올라갈 때
// ./ : 현재 같은 폴더에 있을때

// ex) 
// 현재 컴포넌트(test.vue)에서 assets폴더에 있는 logo.png 파일 import 하기

// 경로
// 현재 컴포넌트 경로 : src/components/test/test1/test.vue
// logo.png 경로 : src/assets/logo.png

// 절대 경로 
import pic from '@/assets/logo.png'
// 상대 경로
// import pic from '../../../assets/logo.png' 

export default {
  data() {
    return {
        pic : pic,
    }
  }    

}
</script>

<style>

</style>