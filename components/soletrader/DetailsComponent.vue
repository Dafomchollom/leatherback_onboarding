<template>
  <AppCardComponent
    title="Business Details"
    subtitle="Fill the remaining Information below"
    width="md"
    button-text="Save and Continue"
    @submit="submitHandler"
  >
    <template #body>
      <form-progress :progress="100" />
      <!-- <a-row type="flex" :gutter="12">
        <a-col :span="12"> </a-col>
        <a-col :span="12"> </a-col>
      </a-row> -->
      <AppInputComponent
        label="Business Name"
        placeholder="Enter Business Name here"
        colon
        required
        name="Business Name"
        type="text"
        :rules="{ required: true }"
        disabled
      />
      <AppInputComponent
        label="Business Registeration Number"
        placeholder="Enter Registeration Number here"
        colon
        required
        name="Business Registeration Number"
        type="text"
        :rules="{ required: true }"
        disabled
      />
      <AppSelectComponent
        label="Annual Business Turnover"
        placeholder="Enter Annual Business Turnover here"
        colon
        required
        name="Annual Business Turnover"
        :remote="false"
        :data="['100,000 - 500,000']"
      />
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
import AppSelectComponent from '@/components/inputcomponents/AppSelectComponent.vue'
import FormProgress from '@/components/uicomponents/FormProgress.vue'
export default Vue.extend({
  name: 'DetailsComponent',
  components: {
    AppCardComponent,
    AppInputComponent,
    FormProgress,
    AppSelectComponent,
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
      this.$emit('businessDetailsSubmit')
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
