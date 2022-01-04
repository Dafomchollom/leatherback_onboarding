<template>
  <div class="default_wrapper">
    <div class="sidebar shadow-md">
      <Sidebar />
    </div>
    <div class="main">
      <div class="circle-icon"></div>
      <div class="default_wrapper__header">
        <!-- <img src="@/assets/images/leatherbacklogo.png" alt="" /> -->
      </div>
      <nuxt style="width: 100%" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Sidebar from '@/components/cooperate/Sidebar.vue'
export default Vue.extend({
  components: {
    Sidebar,
  },
})
</script>

<style lang="scss" scoped>
.main {
  position: relative;
  overflow-x: hidden;
  .circle-icon {
    position: absolute;
    left: 85.07%;
    right: -14.94%;
    top: -14.91%;
    bottom: 70.39%;
    border-radius: 50%;
    border: 50px solid #f4efdf;
  }
}
.default_wrapper {
  height: 100vh;
  width: 100%;
  display: grid;
  grid-template-columns: 350px auto;
  grid-gap: 20px;
  background: url('~/assets/images/homebackground.png');
  background-position: fixed;
  background-size: cover;
  background-repeat: no-repeat;
  .sidebar {
    background: #ffffff;
    position: relative;
  }
  .default_wrapper__header {
    display: flex;
    justify-content: center;
    margin: 15px 0px 20px;
    img {
      width: 232px;
      height: 79px;
    }
  }
  // display: flex;
  // justify-content: center;
  // align-items: center;
}
</style>
