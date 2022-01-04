<template>
  <div>
    <!-- <transition name="slide-fade"> -->
    <component
      :is="currentCardComponent"
      @submit="submitHandler"
      @detailsSubmit="detailsSubmitHandler"
    />
    <!-- </transition> -->
    <!-- <IdentityTypeComponent /> -->
    <!-- <DetailsComponent /> -->
    <!-- <AddressDetailsComponent /> -->
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
// import IdentityTypeComponent from '@/components/individual/IdentityTypeComponent.vue'
// import DetailsComponent from '@/components/individual/DetailsComponent.vue'
// import AddressDetailsComponent from '@/components/individual/AddressDetailsComponent.vue'
// import AppInputComponent from '@/components/inputcomponents/AppInputComponent.vue'

export default Vue.extend({
  components: {
    IdentityTypeComponent: () =>
      import('@/components/individual/IdentityTypeComponent.vue'),
    DetailsComponent: () =>
      import('@/components/individual/DetailsComponent.vue'),
    AddressDetailsComponent: () =>
      import('@/components/individual/AddressDetailsComponent.vue'),
    WelcomeComponent: () =>
      import('@/components/individual/WelcomeComponent.vue'),
  },
  data() {
    return {
      identityType: '',
      step: 'identity',
    }
  },
  computed: {
    currentCardComponent() {
      return this.step === 'identity'
        ? 'IdentityTypeComponent'
        : this.step === 'welcome'
        ? 'WelcomeComponent'
        : 'DetailsComponent'
    },
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
      this.step = 'personal_details'
    },
    detailsSubmitHandler() {
      this.step = 'welcome'
    },
  },
})
</script>
