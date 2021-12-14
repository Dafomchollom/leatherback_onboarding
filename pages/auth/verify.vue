<template>
  <AppCardComponent
    title="Verify Email Address"
    subtitle="Please enter the 6 Digit Confirmation code sent to ola*************.com"
    width="lg"
    button-text="Verify Email"
    @submit="submithandler"
  >
    <template #body>
      <ValidationObserver ref="verifyObserver">
        <AppInputComponent
          label="Token"
          placeholder="Enter Token Here"
          colon
          required
          name="Email Token"
          :rules="{ required: true }"
        />
      </ValidationObserver>
    </template>
  </AppCardComponent>
</template>

<script lang="ts">
import Vue from 'vue'
import { ValidationObserver } from 'vee-validate'
import AppInputComponent from '@/components/inputcomponents/AppInputComponent.vue'
import AppCardComponent from '@/components/uicomponents/AppCardComponent.vue'
export default Vue.extend({
  components: {
    AppCardComponent,
    ValidationObserver,
    AppInputComponent,
  },
  methods: {
    async submithandler() {
      const valid = await this.$refs.verifyObserver?.validate()
      console.log(valid, ':::: valid:::: ')
    },
  },
})
</script>

<style lang="scss" scoped></style>
