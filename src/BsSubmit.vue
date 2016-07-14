<template>
  <div class="form-group" :class="{'has-error': errors}">
    <div :class="inputWrapperClass">
      <button type="submit" class="btn btn-default"><slot><i class="fa fa-floppy-o"></i> Save</slot></button>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      form: {
        type: Object,
        required: true,
      },
    },
    computed: {
      inputWrapperClass () {
        if(this.form.horizontal) {
          return 'col-sm-offset-' + this.form.labelWidth + ' col-sm-' + (12 - this.form.labelWidth)
        }
        return ''
      }
    }
  }
</script>
