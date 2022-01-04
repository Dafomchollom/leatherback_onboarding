<template>
  <div>
    <AppAuthProductTypeComponent @submit="submitHandler" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import AppAuthProductTypeComponent from '@/components/auth/AppAuthProductTypeComponent.vue'
export default Vue.extend({
  components: {
    AppAuthProductTypeComponent,
  },
  methods: {
    submitHandler() {
      this.$router.push('/individual/')
    },
  },
})
</script>

<style lang="scss" scoped></style>
