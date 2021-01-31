<template>
  <div>
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
ul {
  display: flex;
  justify-content: flex-end;
  gap: 16px;
}
.feather {
  position: relative;
  top: 0;
  cursor: pointer;
  padding: 6px;
  margin: 0;
  transition: all 0.1s ease;
  box-sizing: content-box;
  color: var(--color);
  &:hover {
    top: -3px;
    color: var(--link-color);
  }
}
.feather.preferred {
  color: var(--link-color);
}
.feather.selected {
  color: var(--link-color);
}
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
