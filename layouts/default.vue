<template>
  <div class="default_wrapper">
    <div class="default_wrapper__header">
      <img src="@/assets/images/leatherbacklogo.png" alt="" />
    </div>
    <nuxt style="width: 100%" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style lang="scss" scoped>
.default_wrapper {
  height: 100vh;
  width: 100%;
  background: url('~/assets/images/homebackground.png');
  background-position: fixed;
  background-size: cover;
  background-repeat: no-repeat;
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
