<template>
  <div :class="['vx-flexbox', 'vx-tabbar']" onselectstart="return false;">
    <slot></slot>
  </div>
</template>

<script>
import { tab } from 'utils/mixins'
export default {
  componentName: 'Tabbar',
  props: {
    ripple: {
      type: Boolean,
      default: false
    }
  },
  mixins: [tab],
  methods: {
    handleChange (val) {
      if (val !== this.active) {
        this.$emit('update:active', val).$emit('change', val)
      }
    }
  }
}
</script>
