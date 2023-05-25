<template>
  <div class="container">
    <MyHeader />
    <router-view />
    <MyFooter />
  </div>
</template>

<script>
import MyFooter from './components/MyFooter.vue';
import MyHeader from './components/MyHeader.vue';

export default {
  components: {
    MyHeader,
    MyFooter
  }
}

</script>

<style>
#app {
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 24px;
  text-align: center;
  color: #2c3e50;

}

body {
  height: 100%;
}

.container {
  width: 1366px;
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
