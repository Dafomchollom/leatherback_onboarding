<template>
  <AppCardComponent
    title="What Identity do you possess?"
    subtitle="please enter our CAC or TIN number below and we will populate your company intormatior"
    width="md"
    button-text="Save and Continue"
    @submit="submitHandler"
  >
    <template #body>
      <form-progress :progress="50" />
      <div class="identityType_btn leatherback mt-5">
        <label
          :class="{ label_active: identityType === 'cac' }"
          class="shadow-md"
        >
          <img src="@/assets/images/cac_logo.jpeg" alt="" />
          <p class="panel-heading colorOne">CAC Number</p>
          <input
            v-model="identityType"
            type="radio"
            name="cac number"
            value="cac"
            class="card-input-element"
          />
          <a-icon
            v-if="identityType === 'cac'"
            type="check-circle"
            class="checkIcon"
          />
        </label>
      </div>
      <div class="identityType_btn leatherback">
        <label
          :class="{ label_active: identityType === 'tin' }"
          class="shadow-md"
        >
          <img src="@/assets/images/firs-logo-1.png" alt="" />
          <p class="panel-heading colorOne">TIN (Tax Identification Number)</p>
          <input
            v-model="identityType"
            type="radio"
            name="tin number"
            value="tin"
            class="card-input-element"
          />
          <a-icon
            v-if="identityType === 'tin'"
            type="check-circle"
            class="checkIcon"
          />
        </label>
      </div>
      <div class="identityType_btn leatherback mt-5">
        <label
          :class="{ label_active: identityType === 'house' }"
          class="shadow-md"
        >
          <img src="@/assets/images/homelogo.jpeg" alt="" />
          <p class="panel-heading colorOne">House Number</p>
          <input
            v-model="identityType"
            type="radio"
            name="house number"
            value="house"
            class="card-input-element"
          />
          <a-icon
            v-if="identityType === 'house'"
            type="check-circle"
            class="checkIcon"
          />
        </label>
      </div>
      <AppInputComponent
        v-if="identityType === 'house'"
        label="House Address"
        placeholder="Enter House Address here"
        colon
        required
        name="House Address"
        type="text"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'tin'"
        label="Tin(Tax Identification Number)"
        placeholder="Enter TIN here"
        colon
        required
        name="Tax Identification Number"
        type="text"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'cac'"
        label="CAC Number"
        placeholder="Enter CAC Number here"
        colon
        required
        name="CAC Number"
        type="text"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType"
        label="Company Name"
        placeholder="Enter Company Name here"
        colon
        required
        name="Company Name"
        type="text"
        :rules="{ required: true }"
      />
    </template>
  </AppCardComponent>
</template>

<script lang="ts">
import Vue from 'vue'
import AppCardComponent from '@/components/uicomponents/AppCardComponent.vue'
import AppInputComponent from '@/components/inputcomponents/AppInputComponent.vue'
import FormProgress from '@/components/uicomponents/FormProgress.vue'

export default Vue.extend({
  name: 'CompanyIdentityComponent',
  components: {
    AppCardComponent,
    AppInputComponent,
    FormProgress,
  },
  data() {
    return {
      identityType: '',
    }
  },
  watch: {
    identityType: {
      handler(newVal) {
        console.log(newVal, ':::: newVal ::::')
      },
      immediate: true,
    },
  },
  methods: {
    submitHandler() {
      this.$emit('submitCompanyID')
    },
  },
})
</script>

<style lang="scss" scoped>
.identityType_btn {
  label {
    border-radius: 24px;
    // padding: 25px !important;
    display: grid;
    grid-template-columns: 100px auto 20px;
    align-items: center;
    padding: 20px 25px;
    margin-bottom: 15px;
    cursor: pointer;
    transition: all 0.4s;
    border: 1px solid transparent;

    &:hover {
      transform: scale(1.01);
    }
    img {
      width: 64px;
    }
    p {
      margin: 0px;
      font-family: DM Sans;
      font-style: normal;
      font-weight: normal;
      font-size: 18px;
      line-height: 160%;
      color: #0b1320;
    }
    input {
      display: none;
    }
    .checkIcon {
      color: #3365ff;
      font-size: 20px;
    }
  }
  .label_active {
    border: 1px solid #3365ff;
    background: #f7f9ff;
  }
}
</style>
