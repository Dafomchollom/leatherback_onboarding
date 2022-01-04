<template>
  <div class="card-wrapper card-md mx-auto text-center shadow-md">
    <h3 class="card-wrapper__headerWrapper_title">Welcome to Leatherback</h3>
    <h5 class="card-wrapper__headerWrapper_subtitle">
      You have successful onboarded, a NGN Account has been created for you
    </h5>
    <button class="proceed_btn" @click="submitHandler">
      <span> Proceed to Dashboard </span><a-icon type="right" />
    </button>
  </div>
</template>

<script>
export default {
  name: 'WelcomeComponent',
}
</script>

<style lang="scss" scoped>
.card-wrapper {
  background: #ffffff;
  width: 440px;
  padding: 30px 25px;
  border-radius: 10px;
}
.card-wrapper__headerWrapper_title {
  font-family: 'Noe Display';
  font-style: normal;
  font-weight: bold;
  font-size: 24px !important;
  line-height: 130%;
  letter-spacing: 0.03em;
  color: #2e3a59;
}
.card-wrapper__headerWrapper_subtitle {
  font-family: 'DM Sans';
  font-style: normal;
  font-weight: normal;
  font-size: 18px !important;
  line-height: 160%;
  color: #353645;
  margin: 6px 0px;
}
.proceed_btn {
  background: #3365ff;
  color: #ffffff;
  width: 300px;
  border: 1px solid #3365ff;
  padding: 15px 0px;
  margin-top: 40px;
  border-radius: 10px;
}
</style>
