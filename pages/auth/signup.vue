<template>
  <AppCardComponent
    title="Create your accounts in minutes"
    subtitle="Fill the remaining Information below"
    width="lg"
    button-text="Save and Continue"
    @submit="submithandler"
  >
    <template #body>
      <div class="sign-up__header">
        <button
          class="mail_btn"
          :class="{ btn_active: isEmail }"
          @click="isEmail = true"
        >
          <a-icon type="mail" /><span>Email Address</span>
        </button>
        <button
          class="phone_btn"
          :class="{ btn_active: !isEmail }"
          @click="isEmail = false"
        >
          <a-icon type="contacts" /><span>Phone Number</span>
        </button>
      </div>
      <ValidationObserver ref="verifyObserver">
        <AppInputComponent
          v-if="isEmail"
          label="Email"
          placeholder="Enter Email Address here"
          colon
          required
          name="Email Token"
          type="email"
          :rules="{ required: true }"
        />
        <AppInputComponent
          v-if="!isEmail"
          label="Phone Number"
          placeholder="Enter Phone Number here"
          colon
          required
          name="Phone Number"
          type="number"
          :rules="{ required: true }"
        />
        <AppSelectComponent
          label="Entity Type"
          placeholder="Enter Entity Type"
          rules="required"
          name="Entity Type"
          :remote="false"
          :data="['one', 'Two', 'Three']"
          required
        />
        <AppSelectComponent
          label="Select your Country of Operation"
          placeholder="Select your Country of Operation"
          rules="required"
          name="Country of Operation"
          :remote="false"
          :data="['one', 'Two', 'Three']"
          required
        />
        <AppInputComponent
          label="Password"
          placeholder="Create Password"
          colon
          required
          name="Password"
          type="password"
          :rules="{ required: true }"
        />
        <div class="flex align-center pt-3 pb-3">
          <base-checkbox
            id="agreement"
            :checked="isTermsAgreed"
            class="mr-2"
            @change="(value) => (isTermsAgreed = value)"
          />
          <span class="text-base"
            >I agree to Leatherback’s
            <nuxt-link to="/terms-conditions" class="t-cursor-pointer"
              >Terms & Conditions</nuxt-link
            >
            and
            <nuxt-link to="/privacy-policy" class="t-cursor-pointer"
              >Privacy Policy</nuxt-link
            ></span
          >
        </div>
      </ValidationObserver>
    </template>
  </AppCardComponent>
</template>

<script lang="ts">
import Vue from 'vue'
import { ValidationObserver } from 'vee-validate'
import AppInputComponent from '@/components/inputcomponents/AppInputComponent.vue'
import AppSelectComponent from '@/components/inputcomponents/AppSelectComponent.vue'
import AppCardComponent from '@/components/uicomponents/AppCardComponent.vue'
import BaseCheckbox from '@/components/inputcomponents/BaseCheckbox.vue'
export default Vue.extend({
  components: {
    AppCardComponent,
    ValidationObserver,
    AppInputComponent,
    AppSelectComponent,
    BaseCheckbox,
  },
  data() {
    return {
      isEmail: true,
      isTermsAgreed: false,
    }
  },
  methods: {
    async submithandler() {
      const valid = await this.$refs.verifyObserver?.validate()
      // console.log(valid, ':::: valid:::: ')
      this.$router.push('/')
    },
  },
})
</script>

<style lang="scss" scoped>
.sign-up__header {
  display: flex;
  width: 330px;
  border: 1px solid #ced8e2;
  padding: 10px 10px;
  justify-content: center;
  border-radius: 15px;
  margin-bottom: 15px;
  .btn_active {
    background: #3365ff;
    color: #fff;
  }
  .mail_btn {
    margin-right: 10px;
  }
  button {
    width: 100%;
    max-width: 150px;
    padding: 15px 15px;
    display: flex;
    border-radius: 15px;
    justify-content: space-between;
    align-items: center;
    transition: all 0.5s;
    font-family: 'Public Sans';
    font-style: normal;
    font-weight: 600;
    font-size: 14px;
    line-height: 19px;
    letter-spacing: -0.285714px;
    color: #6e7786;
    span {
      margin-left: 5px;
    }
  }
}
</style>
