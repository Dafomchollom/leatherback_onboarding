<template>
  <div
    class="md:container md:mx-auto bg-white rounded-lg shadow-md productType_wrapper"
  >
    <div class="productType_wrapper__header text-center">
      <!-- <button><img src="@/assets/images/ic_Dropdown.svg" alt="" /></button> -->
      <h2 class="productType_wrapper__header__title">
        Select Which of our Products you’re interested in
      </h2>
      <p class="productType_wrapper__header__subtitle">
        Choose from one of your products
      </p>
    </div>
    <div class="productType_wrapper__body">
      <div
        class="productType_wrapper__body__card shadow-md leatherback"
        :class="{
          productType_wrapper__body__cardActive: productType === 'leatherback',
        }"
      >
        <label>
          <input
            v-model="productType"
            type="radio"
            name="product"
            value="leatherback"
            class="card-input-element"
          />

          <div class="panel panel-default card-input">
            <div class="panel-heading colorOne">Leatherback</div>
            <div class="panel-body">
              Easy-to-use multi-currency account optimized for Individuals,
              SMEs, local corporations.
            </div>
            <div class="pannel-footer">
              <span class="colorOne">Select Leatherback</span>
            </div>
          </div>
        </label>
        <img src="@/assets/images/producttypeimage.svg" alt="" />
      </div>
      <div
        class="productType_wrapper__body__card payr"
        :class="{
          productType_wrapper__body__cardActive: productType === 'payr',
        }"
      >
        <label>
          <input
            v-model="productType"
            type="radio"
            name="product"
            value="payr"
            class="card-input-element"
          />

          <div class="panel panel-default card-input">
            <div class="panel-heading colorTwo">PayR</div>
            <div class="panel-body">
              Easy-to-use multi-currency account optimized for Individuals,
              SMEs, local corporations.
            </div>
            <div class="pannel-footer">
              <span class="colorTwo">Select Leatherback</span>
            </div>
          </div>
        </label>
        <img src="@/assets/images/producttypeimage.svg" alt="" />
      </div>
    </div>
    <div class="productType_wrapper__footer">
      <button class="submit-btn shadow-md" @click="submitHandler">
        <span>Continue</span><a-icon type="right" />
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'AppAuthProductTypeComponent',
  data() {
    return {
      productType: '',
    }
  },
  watch: {
    productType: {
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
.productType_wrapper {
  background: #ffffff;
  width: 100%;
  height: auto;
  padding: 20px 40px;
  max-width: 850px;
  .productType_wrapper__header {
    button img {
      widows: 48px;
      height: 48px;
    }
    .productType_wrapper__header__title {
      font-family: 'NoeDisplay';
      font-size: 28px;
      color: #2e3a59;
      margin: 15px 0px 2px;
    }
    .productType_wrapper__header__subtitle {
      font-family: 'DM Sans', sans-serif;
      font-size: 23px;
      color: #353645;
    }
  }
  .productType_wrapper__body {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;

    .productType_wrapper__body__card {
      position: relative;
      width: 48%;
      border-radius: 30px;
      overflow: hidden;
      transition: all 0.4s !important;
      border: 2px solid transparent;
      label {
        width: 100%;
        height: 293px;
      }
      .card-input-element {
        display: none;
      }

      .card-input {
        margin: 10px;
        height: 293px;
        position: relative;
        z-index: 1;
        padding: 30px 25px;
        border-radius: 30px;
        display: relative;
        .colorOne {
          color: #3365ff;
        }
        .colorTwo {
          color: #48b5e8;
        }
        .panel-heading {
          font-family: 'Noe Display';
          font-style: normal;
          font-weight: bold;
          font-size: 24px;
          line-height: 25px;
          letter-spacing: 1px;
        }
        .panel-body {
          font-family: 'DM Sans';
          font-style: normal;
          font-weight: normal;
          font-size: 16px;
          line-height: 27px;
          letter-spacing: -0.01em;
          color: #010101;
          margin-top: 10px;
        }
        .pannel-footer {
          position: absolute;
          bottom: 0%;
          left: 0%;
          padding: 30px 25px;
          span {
            background: #ffffff;
            border-radius: 14px;
            font-family: 'DM Sans';
            font-style: normal;
            font-weight: bold;
            font-size: 16px;
            line-height: 100%;
            letter-spacing: -0.02em;
            padding: 12px 21.5px;
          }
        }
      }

      .card-input:hover {
        cursor: pointer;
      }

      .card-input-element:checked + .card-input {
        // box-shadow: 0 0 1px 1px #2ecc71;
        // width: 100%;
      }
      img {
        position: absolute;
        bottom: 0px;
        z-index: 0;
        right: 0px;
      }
    }
    .productType_wrapper__body__cardActive {
      border: 2px solid var(--brand-blue);
    }
    .leatherback {
      background: #d9e2fd;
    }
    .payr {
      background: #daf0fa;
    }
  }
  .productType_wrapper__body__card:hover {
    transform: scale(1.01);
  }
  .productType_wrapper__footer {
    margin-top: 35px;
    margin-bottom: 20px;
    button {
      background: #3365ff;
      border-radius: 24px;
      padding: 20px 25px;
      width: 300px;
      font-family: 'DM Sans';
      font-style: normal;
      font-weight: bold;
      font-size: 18px;
      line-height: 100%;
      letter-spacing: -0.02em;
      color: #ffffff;
      display: flex;
      justify-content: space-between;
      transition: all 0.5s;
    }
    button:hover {
      padding: 20px;
    }
  }
}
</style>
