<template>
  <div
    :class="{ 'card-lg': width === 'lg', 'card-md': width === 'md' }"
    class="md:container md:mx-auto bg-white rounded-lg p-10 shadow-md"
  >
    <div class="card-wrapper__headerWrapper">
      <h3 class="card-wrapper__headerWrapper_title">{{ title }}</h3>
      <h5 v-if="subtitle" class="card-wrapper__headerWrapper_subtitle">
        {{ subtitle }}
      </h5>
    </div>
    <div class="card-wrapper__body">
      <slot name="body"> </slot>
    </div>
    <div class="card-wrapper__footer">
      <button class="back_btn" @click="backHandler">
        <a-icon type="left" /><span>Go Back </span>
      </button>
      <button class="proceed_btn" @click="submitHandler">
        <span>{{ buttonText }}</span
        ><a-icon type="right" />
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'AppCardComponent',
  components: {},
  props: {
    width: {
      type: String,
      required: true,
      default: 'lg',
    },
    title: {
      type: String,
      required: true,
      default: '',
    },
    subtitle: {
      type: String,
      required: false,
      default: '',
    },
    buttonText: {
      type: String,
      required: true,
      default: 'Save and Continue',
    },
  },

  methods: {
    backHandler() {
      this.$emit('back')
    },
    submitHandler() {
      this.$emit('submit')
    },
  },
})
</script>

<style lang="scss" scoped>
.card-wrapper {
  background: #ffffff;
  width: 100%;
}
.card-wrapper__headerWrapper {
  margin-bottom: 20px;
  .card-wrapper__headerWrapper_title {
    font-family: 'Noe Display';
    font-style: normal;
    font-weight: bold;
    font-size: 24px;
    line-height: 130%;
    letter-spacing: 0.03em;
    color: #2e3a59;
  }
  .card-wrapper__headerWrapper_subtitle {
    font-family: 'DM Sans';
    font-style: normal;
    font-weight: normal;
    font-size: 18px;
    line-height: 160%;
    color: #353645;
    margin: 6px 0px;
  }
}
.card-wrapper__footer {
  display: flex;
  margin-top: 30px;
  .proceed_btn {
    background: #3365ff;
    color: #ffffff;
    width: 300px;
    border: 1px solid #3365ff;
  }
  .back_btn {
    border: 1px solid #e2e8f5;
    margin-right: 15px;
    width: 170px;
  }
  button {
    display: flex;
    border-radius: 15px;
    padding: 25px 30px;
    font-family: 'DM Sans';
    font-style: normal;
    font-weight: bold;
    font-size: 18px;
    line-height: 100%;
    letter-spacing: -0.02em;
    display: flex;
    justify-content: space-between;
    transition: all 0.5s;
  }
  button:hover {
    padding: 25px;
  }
}
.card-lg {
  max-width: 840px;
}
.card-md {
  max-width: 640px;
}
</style>
