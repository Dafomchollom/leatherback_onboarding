<template>
  <div class="md-checkbox center_align_row matte">
    <input
      :id="id"
      type="checkbox"
      :checked="checked"
      @change="$emit('change', $event.target.checked)"
    />
    <label :for="id" class="t--mt-1" :class="[labelClasses]">
      <slot />
    </label>
  </div>
</template>

<script>
export default {
  model: {
    prop: 'checked',
    event: 'change',
  },
  props: {
    id: {
      type: String,
      default: '',
    },
    checked: {
      type: Boolean,
      default: false,
    },
    labelClasses: {
      type: String,
      default: '',
      required: false,
    },
  },
}
</script>

<style scoped>
.md-checkbox {
  position: relative;
  text-align: left;
}
.md-checkbox.md-checkbox-inline {
  display: inline-block;
}
.md-checkbox label {
  cursor: pointer;
  clear: both;
  padding-left: 1px;
}
.md-checkbox label:not(:empty) {
  padding-left: 0.75em;
}
.md-checkbox label:before,
.md-checkbox label:after {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
}
.md-checkbox label:before {
  width: 1.5em;
  height: 1.5em;
  background: var(--brand-light-blue);
  border: 1.45px solid #6ea0f7;
  border-radius: 0.13em;
  cursor: pointer;
  transition: background 0.3s;
}
.md-checkbox input[type='checkbox'] {
  outline: 0;
  visibility: hidden;
  width: 1.5em;
  margin: 0;
  display: block;
  float: left;
}
.md-checkbox input[type='checkbox']:checked + label:before {
  background: var(--brand-blue);
  border: none;
}
.md-checkbox input[type='checkbox']:checked + label:after {
  transform: translate(0.25em, 0.3365384615em) rotate(-45deg);
  width: 1em;
  height: 0.4em;
  border: 0.125em solid #fff;
  border-top-style: none;
  border-right-style: none;
  transition: all 0.5s;
}
.md-checkbox input[type='checkbox']:disabled + label:before {
  border-color: rgba(0, 0, 0, 0.2);
}
.md-checkbox input[type='checkbox']:disabled:checked + label:before {
  background: rgba(0, 0, 0, 0.2);
}
</style>
