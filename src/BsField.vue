<template>
  <div class="form-group" :class="{'has-error': errors}">
    <label :class="labelClass" :for="name" v-if="label">{{ label }}</label>
    <div :class="inputWrapperClass">
      <vue-select v-if="choices" :options="choices">
      </vue-select>
      <input :class="{'form-control': type != 'checkbox'}" :placeholder="placeholder" :type="inputType" :id="name" @key.enter="$dispatch('bs-form.trigger-submit')" v-model="value" v-else>
      <p class="help-block" v-for="error in errors">{{ error }}</p>
      <p class="help-block" v-if="helpText">{{ helpText }}</p>
    </div>
  </div>
</template>

<script>
  import BsForm from './BsForm'
  import VueSelect from 'vue-select'

  export default {
    components: {
      VueSelect,
    },
    props: {
      name: {
        type: String,
        required: true,
      },
      type: {
        type: String,
        required: true,
      },
      label: String,
      helpText: String,
      placeholder: String,
      form: {
        type: Object,
        required: true,
      },
      choices: Array,
      errors: Array,
    },
    data () {
      return {
        value: '',
      }
    },
    ready () {
      this.sendValue()
    },
    watch: {
      value (val, oldVal) {
        this.sendValue()
      },
    },
    methods: {
      sendValue () {
        this.$dispatch('bs-field.value-changed', {name: this.name, value: this.value})
      },
    },
    computed: {
      labelClass () {
        if(this.form.horizontal) {
          return 'col-sm-' + this.form.labelWidth + ' control-label'
        }
        return ''
      },
      inputWrapperClass () {
        if(this.form.horizontal) {
          return 'col-sm-' + (12 - this.form.labelWidth)
        }
        return ''
      },
      inputType () {
        if(this.type == 'integer') return 'number'
        return this.type
      }
    }
  }
</script>
