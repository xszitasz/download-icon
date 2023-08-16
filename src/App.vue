<template>
  <div id="app">
    <!-- Dummy Data Example 1 (PDF) -->
    <DownloadIcon 
      :fileType="'pdf'" 
      :file="'https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf'" 
      :docName="'Dummy PDF Document'" />

    <!-- Dummy Data Example 2 (TXT) -->
    <DownloadIcon 
      :fileType="'txt'" 
      :file="'https://catfact.ninja/fact'" 
      :docName="'Dummy TXT Archive'" />
  </div>
</template>

<script>
import DownloadIcon from './components/DownloadIcon.vue';

export default {
  name: 'App',
  components: {
    DownloadIcon
  }
};
</script>

<style>
#app {
  min-height: calc(100vh);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
