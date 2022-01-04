<template>
  <AppCardComponent
    title="What Identity do you possess?"
    subtitle="Fill the remaining Information below"
    width="md"
    button-text="Save and Continue"
  >
    <template #body>
      <form-progress :progress="100" />
      <AppInputComponent
        label="Registered Business Address"
        placeholder="Enter Registered Business Address here"
        colon
        required
        name="Business Address"
        type="text"
      />
      <AppInputComponent
        label="Registered Business Address Line 2"
        placeholder="Enter Registered Business Address here"
        colon
        required
        name="Business Address"
        type="text"
      />
      <a-row type="flex" :gutter="12">
        <a-col :span="12">
          <AppInputComponent
            label="Region/State"
            placeholder="Enter Region/State here"
            colon
            required
            name="Region or State"
            type="text"
            :rules="{ required: true }"
            disabled
          />
        </a-col>
        <a-col :span="12">
          <AppInputComponent
            label="Town/City"
            placeholder="Enter Town City here"
            colon
            required
            name="Town and City"
            type="text"
            :rules="{ required: true }"
            disabled
          />
        </a-col>
      </a-row>
      <AppInputComponent
        label="Postal Code"
        placeholder="Enter Postal Code here"
        colon
        required
        name="Postal Code"
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
  name: 'AddressDetailsComponent',
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
})
</script>

<style lang="scss" scoped>
.identityType_btn {
  label {
    border-radius: 24px;
    padding: 25px !important;
    display: grid;
    grid-template-columns: 100px auto 20px;
    align-items: center;
    padding: 10px;
    margin-bottom: 15px;
    cursor: pointer;
    transition: all 0.4s;
    border: 1px solid transparent;

    &:hover {
      transform: scale(1.01);
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
