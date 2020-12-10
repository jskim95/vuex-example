<template>
  <div id="app">
    <test-root></test-root>
    <region-buttons></region-buttons>
    <country-list></country-list>
  </div>
</template>

<script>
import RegionButtons from './components/RegionButtons';
import CountryList from './components/CountryList'
import testRoot from './components/test/test1/test'
export default {
  name: 'App',
  components : {RegionButtons, CountryList, testRoot}
}
</script>

<style>
</style>
