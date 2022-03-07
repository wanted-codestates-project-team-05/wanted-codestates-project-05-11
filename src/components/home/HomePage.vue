<template>
  <div id="home">
    <main-header />
    <search-info v-model="company" />
    <search-input v-model="company" />
  </div>
</template>

<script>
import SearchInput from './SearchInput.vue';
import SearchInfo from './SearchInfo.vue';
import MainHeader from './MainHeader.vue';

export default {
  name: 'home-page',
  components: {
    MainHeader,
    SearchInput,
    SearchInfo,
  },
  data() {
    return {
      company: '',
    };
  },
};
</script>

<style>
#home {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  max-width: 360px;
  display: flex;
  flex-direction: column;
}
</style>
