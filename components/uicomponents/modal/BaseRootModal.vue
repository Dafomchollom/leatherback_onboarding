<template>
  <base-modal
    :is-open="!!component"
    :title="title"
    :show-footer="showFooter"
    :modal-size="modalSize"
    @onClose="handleClose"
    @onCloseFromOutside="handleOutsideModalClick"
  >
    <component :is="component" v-bind="props" @onClose="handleClose" />
  </base-modal>
</template>

<script>
import BaseModal from './BaseModal.vue';

export default {
  components: {
    BaseModal,
  },
  data() {
    return {
      component: null,
      title: '',
      props: null,
      closeOnBodyClick: true,
      showFooter: false,
      modalSize: 'small', // small, medium, large
    };
  },
  mounted() {
    this.$ModalBus.$on(
      'open-modal',
      ({
        component,
        title = '',
        closeOnBodyClick = true,
        showFooter = false,
        props = null,
        modalSize = 'medium',
      }) => {
        this.component = component;
        this.title = title;
        this.props = props;
        this.closeOnBodyClick = closeOnBodyClick;
        this.showFooter = showFooter;
        this.modalSize = modalSize;
      }
    );
    document.addEventListener('keyup', this.handleKeyup);
  },
  beforeDestroy() {
    document.removeEventListener('keyup', this.handleKeyup);
  },
  methods: {
    handleOutsideModalClick() {
      // console.log('closing');
      if (!this.closeOnBodyClick) return;
      this.handleClose();
    },
    handleClose() {
      this.title = '';
      this.component = null;

      // do something when modal is closed
      this.$ModalBus.$emit('modal-closed');
    },
    handleKeyup(e) {
      if (e.keyCode === 27) this.handleClose();
    },
  },
};
</script>
