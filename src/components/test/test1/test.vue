<template>
  <div>
    <img :src="pic">  
  </div>
</template>

<script>
// @ : src(루트)부터 시작
// ../ : 상위 폴더로 올라갈 때
// ./ : 현재 같은 폴더에 있을때

// ex) 
// 현재 컴포넌트에서 assets폴더에 있는 logo.png 파일 import 하기

// 절대 경로 
// import pic from '@/assets/logo.png'
// 상대 경로
import pic from '../../../assets/logo.png' 

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