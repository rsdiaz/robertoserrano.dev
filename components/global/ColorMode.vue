<template>
  <div class="">
    <ul>
      <li
        v-for="color of colors"
        :key="color"
        @click="$colorMode.preference = color"
      >
        <component
          :is="`icon-${color}`"
          :class="getClasses(color)"
          @click="$colorMode.preference = color"
        />
      </li>
    </ul>
    <!-- <ColorScheme placeholder="..." tag="span">
      Color mode:
      <b>{{ $colorMode.preference }}</b>
      <span v-if="$colorMode.preference === 'system'">
        (
        <i>{{ $colorMode.value }}</i> mode detected)
      </span>
    </ColorScheme> -->
  </div>
</template>
<style lang="scss" scoped>
@import '~/assets/scss/components/color-mode.scss';
</style>

<script>
import IconSystem from '@/assets/icons/system.svg?inline'
import IconLight from '@/assets/icons/light.svg?inline'
import IconDark from '@/assets/icons/dark.svg?inline'

export default {
  components: {
    IconSystem,
    IconLight,
    IconDark,
  },
  data() {
    return {
      colors: ['system', 'light', 'dark'],
    }
  },
  methods: {
    getClasses(color) {
      if (this.$colorMode.unknown) {
        return {}
      }
      return {
        preferred: color === this.$colorMode.preference,
        selected: color === this.$colorMode.value,
      }
    },
  },
}
</script>
