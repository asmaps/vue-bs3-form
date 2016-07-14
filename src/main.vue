<script>
  import BsForm from './BsForm'
  import BsField from './BsField'
  import BsSubmit from './BsSubmit'

  export default {
    BsForm,
    BsField,
    BsSubmit,
    install (Vue, options) {
      Vue.component('bs-form', BsForm)
      Vue.component('bs-field', BsField)
      Vue.component('bs-submit', BsSubmit)
    }
  }
</script>
