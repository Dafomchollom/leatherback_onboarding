<template>
  <div>
    <AppCardComponent
      title="Key Controller Directors"
      subtitle="Fill the remaining Information below"
    >
      <template #body>
        <a-row type="flex" :gutter="12">
          <a-col :span="12" class="mb-2">
            <button class="add_btn" @click="visible = true">
              <!-- <a-icon type="plus-circle" class="plus-icon" /> -->
              <span class="add_btn_icon">+</span>
              <p>Add Another Director</p>
            </button>
          </a-col>
          <a-col :span="12" class="mb-2">
            <div class="key_controller_card">
              <!-- <a-icon type="plus-circle" class="plus-icon" /> -->
              <div class="key_controller_card_details">
                <span class="initials">OO</span>
                <div class="details_wrapper">
                  <p class="name">Olaniyi Oladokun</p>
                  <p class="email">oladokuniyi@gmail.com</p>
                </div>
              </div>
              <p class="job_role">Managing Director</p>
            </div>
          </a-col>
          <a-col :span="12" class="mb-2">
            <div class="key_controller_card">
              <!-- <a-icon type="plus-circle" class="plus-icon" /> -->
              <div class="key_controller_card_details">
                <span class="initials">OO</span>
                <div class="details_wrapper">
                  <p class="name">Olaniyi Oladokun</p>
                  <p class="email">oladokuniyi@gmail.com</p>
                </div>
              </div>
              <p class="job_role">Managing Director</p>
            </div>
          </a-col>
          <a-col :span="12" class="mb-2">
            <div class="key_controller_card">
              <!-- <a-icon type="plus-circle" class="plus-icon" /> -->
              <div class="key_controller_card_details">
                <span class="initials">OO</span>
                <div class="details_wrapper">
                  <p class="name">Olaniyi Oladokun</p>
                  <p class="email">oladokuniyi@gmail.com</p>
                </div>
              </div>
              <p class="job_role">Managing Director</p>
            </div>
          </a-col>
        </a-row>
      </template>
    </AppCardComponent>
    <base-modal
      :is-open="visible"
      :footer="null"
      :width="670"
      @onClose="handleClose"
      @onCloseFromOutside="handleOutsideModalClick"
    >
      <AppCardComponent
        title="Add Key Controller Director"
        subtitle="Fill the remaining Information below"
        width="md"
        button-text="Save and Continue"
      >
        <template #body>
          <a-row type="flex" :gutter="12">
            <a-col :span="12">
              <AppInputComponent
                label="Firt Name"
                placeholder="Enter First Name here"
                colon
                required
                name="First Name"
                type="text"
                :rules="{ required: true }"
                disabled
              />
            </a-col>
            <a-col :span="12">
              <AppInputComponent
                label="Last Name"
                placeholder="Enter Last Name here"
                colon
                required
                name="Last Name"
                type="text"
                :rules="{ required: true }"
                disabled
              />
            </a-col>
          </a-row>
          <AppInputComponent
            label="Middle Name"
            placeholder="Enter Middle Name here"
            colon
            required
            name="Middle Name"
            type="text"
          />
          <AppInputComponent
            label="Residential Address"
            placeholder="Enter Residential Address here"
            colon
            required
            name="Residential Address"
            type="text"
            :rules="{ required: true }"
          />
        </template>
      </AppCardComponent>
    </base-modal>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import BaseModal from '@/components/uicomponents/modal/BaseModal.vue'
import AppCardComponent from '@/components/uicomponents/AppCardComponent.vue'
import AppInputComponent from '@/components/inputcomponents/AppInputComponent.vue'

export default Vue.extend({
  components: {
    AppCardComponent,
    AppInputComponent,
    BaseModal,
  },
  data() {
    return {
      visible: false,
    }
  },
  methods: {
    showModal() {
      this.visible = true
    },
    handleOk() {
      this.visible = false
    },
  },
})
</script>

<style lang="scss" scoped>
.add_btn {
  border: 2px solid #e0e0e0;
  width: 100%;
  height: 100%;
  //   background: red;
  outline: none;
  border-radius: 16px;
  padding: 25px 0px;
  color: #3365ff;
  .add_btn_icon {
    font-size: 25px;
    border: 2px solid #e0e0e0;
    border-radius: 100%;
    padding: 5px 15px;
  }
  p {
    margin: 20px 0px 0px;
    font-family: 'DM Sans';
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 21px;
  }
}
.key_controller_card {
  border: 2px solid #e0e0e0;
  width: 100%;
  border-radius: 16px;
  padding: 25px;
  .key_controller_card_details {
    display: grid;
    grid-template-columns: 50px auto;
    grid-gap: 10px;
    text-align: start;
    align-items: center;
    .initials {
      background: #ff5663;
      color: #ffffff;
      font-size: 16px;
      height: 50px;
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;
    }
    .details_wrapper {
      margin: auto 0px;
      .name {
        font-family: 'DM Sans';
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 21px;
        color: #2e3a59;
        margin-bottom: 3px;
      }
      .email {
        font-family: 'DM Sans';
        font-style: normal;
        font-weight: normal;
        font-size: 13px;
        line-height: 17px;
        margin: 0px;
      }
    }
  }
  .job_role {
    text-align: start;
    color: #353645;
    font-family: 'DM Sans';
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 16px;
    margin-top: 12px;
    margin-bottom: 0px;
  }
}
</style>
