<template>
  <form :class="{'form-inline': inline, 'form-horizontal': horizontal}" @submit.prevent="$emit('bs-form.trigger-submit')" v-el:form>
    <slot></slot>
  </form>
</template>

<script>
  export default {
    props: {
      inline: Boolean,
      horizontal: Boolean,
      labelWidth: {
        type: Number,
        default: 2,
      },
    },
    data () {
      return {
        formData: {}
      }
    },
    events: {
      'bs-form.trigger-submit' () {
        this.$dispatch('bs-form.submit', this.formData)
      },
      'bs-field.value-changed' (data) {
        this.$set('formData.' + data.name, data.value)
      }
    }
  }
</script>
