<template>
  <div>
    <img src="@/assets/images/leatherbacklogo.png" alt="" />
    <div class="sidebar_body">
      <h2 class="sidebar_header">Create your account in minutes</h2>
      <ul class="nav-wrapper">
        <li class="nav-item">
          <span class="number">1</span>
          <div>
            <h2 class="nav-title">Personal Information</h2>
            <p class="nav-description">
              consectetur adipiscing elit, sed do eiusmod tempor incididunt
            </p>
          </div>
        </li>
        <li class="nav-item">
          <span class="number">2</span>
          <div>
            <h2 class="nav-title">Business Information</h2>
          </div>
        </li>
      </ul>
    </div>
    <img
      src="@/assets/images/producttypeimage.svg"
      class="sidebar-footer-img"
      alt=""
    />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({})
</script>

<style lang="scss" scoped>
.sidebar_header {
  font-family: Noe Display;
  font-style: normal;
  font-weight: bold;
  font-size: 28px;
  line-height: 160%;
  color: #0b1320;
}
.sidebar_body {
  padding: 20px 25px;
  .nav-item {
    margin: 20px 0px;
    display: grid;
    grid-template-columns: 25px auto;
    grid-gap: 15px;
    .number {
      border: 1px solid #005ef6;
      color: #005ef6;
      height: 25px;
      width: 25px;
      display: flex;
      border-radius: 50%;
      justify-content: center;
      align-items: center;
    }
    .nav-title {
      font-family: 'DM Sans';
      font-style: normal;
      font-weight: 500;
      font-size: 18px;
      line-height: 28px;
      color: #141922;
      margin: 0px;
    }
    .nav-description {
      font-family: 'DM Sans';
      font-style: normal;
      font-weight: normal;
      font-size: 14px;
      line-height: 160%;
      color: #747474;
    }
  }
}
.sidebar-footer-img {
  position: absolute;
  bottom: 0;
  right: 0;
}
</style>
