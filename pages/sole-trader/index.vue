<template>
  <div>
    <!-- <KeyControllers /> -->
    <!-- <IdentityTypeComponent /> -->
    <!-- <ContactDetailsComponent /> -->
    <!-- <CompanyIdentityComponent /> -->
    <!-- <CompanyIdentityComponent /> -->
    <component
      :is="currentCardComponent"
      @submit="submitHandler"
      @detailsSubmit="detailsSubmitHandler"
      @businessDetailsSubmit="businessDetailsSubmitHandler"
      @submitCompanyID="companyIdSubmitHandler"
    />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
// import KeyControllers from '@/components/cooperate/KeyControllers.vue'
// import AddressDetailsComponent from '@/components/cooperate/AddressDetailsComponent.vue'
// import DetailsComponent from '@/components/cooperate/DetailsComponent.vue'
// import IdentityTypeComponent from '@/components/cooperate/IdentityTypeComponent.vue'
// import ContactDetailsComponent from '@/components/cooperate/ContactDetailsComponent.vue'
export default Vue.extend({
  components: {
    // AddressDetailsComponent,
    // DetailsComponent,
    KeyControllers: () => import('@/components/soletrader/KeyControllers.vue'),
    IdentityTypeComponent: () =>
      import('@/components/soletrader/IdentityTypeComponent.vue'),
    ContactDetailsComponent: () =>
      import('@/components/soletrader/ContactDetailsComponent.vue'),
    CompanyIdentityComponent: () =>
      import('@/components/soletrader/CompanyIdentityComponent.vue'),
    DetailsComponent: () =>
      import('@/components/soletrader/DetailsComponent.vue'),
    // CompanyIdentityComponent: () =>
    //   import('@/components/cooperate/CompanyIdentityComponent.vue'),
    // KeyControllers,
  },
  layout: 'soletrader_layout',

  data() {
    return {
      step: 'identity',
    }
  },
  computed: {
    currentCardComponent() {
      return this.step === 'identity'
        ? 'IdentityTypeComponent'
        : this.step === 'company_identity'
        ? 'CompanyIdentityComponent'
        : this.step === 'business_details'
        ? 'DetailsComponent'
        : this.step === 'key_controllers'
        ? 'KeyControllers'
        : this.step === 'welcome'
        ? 'WelcomeComponent'
        : 'ContactDetailsComponent'
    },
  },
  methods: {
    submitHandler() {
      this.step = 'personal_details'
    },
    detailsSubmitHandler() {
      this.step = 'company_identity'
    },
    companyIdSubmitHandler() {
      this.step = 'business_details'
    },
    businessDetailsSubmitHandler() {
      this.step = 'key_controllers'
    },
  },
})
</script>

<style></style>
