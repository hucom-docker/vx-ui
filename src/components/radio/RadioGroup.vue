<template>
  <div :class="['vx-radio-group', {'is-divider': divider, 'is-disabled': disabled}]">
    <slot></slot>
  </div>
</template>

<script>
import { input } from 'utils/mixins'

export default {
  componentName: 'RadioGroup',
  mixins: [input],
  props: {
    ...input.props,
    divider: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    handleChange (value) {
      this.$emit('input', value).$emit('change', value)
      this.eDispatch('ElFormItem', 'el.form.blur', [value])
      this.eDispatch('ElFormItem', 'el.form.change', [value])
    }
  }
}
</script>
