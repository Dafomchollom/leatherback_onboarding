<template>
  <AppCardComponent
    title="What Identity do you possess?"
    width="md"
    button-text="Save and Continue"
    @submit="submitHandler"
  >
    <template #body>
      <div class="identityType_btn leatherback">
        <label
          :class="{ label_active: identityType === 'driversLicence' }"
          class="shadow-md"
        >
          <img src="@/assets/images/driverlicencelogo.svg" alt="" />
          <p class="panel-heading colorOne">Drivers License</p>
          <input
            v-model="identityType"
            type="radio"
            name="product"
            value="driversLicence"
            class="card-input-element"
          />
          <a-icon
            v-if="identityType === 'driversLicence'"
            type="check-circle"
            class="checkIcon"
          />
        </label>
      </div>
      <div class="identityType_btn leatherback">
        <label
          :class="{ label_active: identityType === 'nin' }"
          class="shadow-md"
        >
          <img src="@/assets/images/nimclogo.svg" alt="" />
          <p class="panel-heading colorOne">NIN</p>
          <input
            v-model="identityType"
            type="radio"
            name="nin"
            value="nin"
            class="card-input-element"
          />
          <a-icon
            v-if="identityType === 'nin'"
            type="check-circle"
            class="checkIcon"
          />
        </label>
      </div>
      <div class="identityType_btn leatherback">
        <label
          :class="{ label_active: identityType === 'inverite' }"
          class="shadow-md"
        >
          <img src="@/assets/images/inverite_logo.png" alt="" />
          <p class="panel-heading colorOne">Inverite</p>
          <input
            v-model="identityType"
            type="radio"
            name="inverite"
            value="inverite"
            class="card-input-element"
          />
          <a-icon
            v-if="identityType === 'inverite'"
            type="check-circle"
            class="checkIcon"
          />
        </label>
      </div>
      <AppInputComponent
        v-if="identityType === 'driversLicence'"
        label="Identification Number"
        placeholder="Enter Identification Number here"
        colon
        required
        name="Identification Number"
        type="email"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'driversLicence'"
        label="First Name"
        placeholder="Enter First Name here"
        colon
        required
        name="First Name"
        type="text"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'driversLicence'"
        label="Last Name"
        placeholder="Enter Last Name here"
        colon
        required
        name="Last Name"
        type="text"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'driversLicence'"
        label="Date Of Birth(dd/mm/yyyy)"
        placeholder="Enter DOB here"
        colon
        required
        name="Date Of Birth"
        type="date"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'nin'"
        label="Identification Number"
        placeholder="Enter Identification Number here"
        colon
        required
        name="Identification Number"
        type="text"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'nin'"
        label="Company Name"
        placeholder="Enter Company Name here"
        colon
        required
        name="Company Name"
        type="text"
        :rules="{ required: true }"
      />
      <AppInputComponent
        v-if="identityType === 'inverite'"
        label="Account Number"
        placeholder="Enter Account Number here"
        colon
        required
        name="Account Number"
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
export default Vue.extend({
  name: 'IdentityTypeComponent',
  components: {
    AppCardComponent,
    AppInputComponent,
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
      this.$emit('submit')
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
