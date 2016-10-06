<template>
  <svg version="1.1" class="octicon" :class="clazz" :role="label ? 'img' : 'presentation'" :aria-label="label" :width="width" :height="height" :viewBox="box" :style="style">
    <path :d="icon.d" />
  </svg>
</template>

<style>
.octicon {
  display: inline-block;
  fill: currentColor;
}

.octicon.flip-horizontal {
  transform: scale(-1, 1);
}

.octicon.flip-vertical {
  transform: scale(1, -1);
}

.octicon.spin {
  animation: octicon-spin 1s 0s infinite linear;
}

@keyframes octicon-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>

<script>
import OCTICONS from '../assets/octicons'

// can register custom icons
let icons = OCTICONS

export default {
  props: {
    name: {
      type: String,
      required: true,
      validator: function (val) {
        return val in OCTICONS;
      }
    },
    scale: {
      type: Number,
      default: 1,
      coerce: function (val) {
        val = Number(val)
        return isNaN(val) ? undefined : val;
      },
      validator: function (val) {
        return Number(val) > 0
      }
    },
    spin: Boolean,
    flip: {
      validator: function (val) {
        return val === 'horizontal' || val === 'vertical'
      }
    },
    label: String
  },
  computed: {
    clazz: function () {
      return {
        spin: this.spin,
        'flip-horizontal': this.flip === 'horizontal',
        'flip-vertical': this.flip === 'vertical'
      }
    },
    icon: function () {
      return icons[this.name]
    },
    box: function () {
      return `0 0 ${this.icon.width} ${this.icon.height}`
    },
    width: function () {
      return this.icon.width * this.scale
    },
    height: function () {
      return this.icon.height * this.scale
    },
    style: function () {
      if (this.scale === 1) {
        return false
      }
      return {
        fontSize: this.scale + 'em'
      }
    }
  },
  register: function (custom) {
    for (let name in custom) {
      icons[name] = custom[name]
    }
  }
}
</script>
