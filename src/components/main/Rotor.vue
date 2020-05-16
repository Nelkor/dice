<template>
  <div class="rotor">
    <div class="stator"></div>

    <RotorItem
      v-for="(name, key) of sections"
      :key="key"
      :text="name"
      :active="key == current"
      :angle="angle(key)"
      :to="origin + key"
    />
  </div>
</template>

<script>
import RotorItem from '@/components/main/RotorItem'

const reverse = angle => angle > 0 ? angle - 360 : angle + 360

export default {
  name: 'Rotor',
  props: {
    sections: Object,
    current: String,
    origin: String,
  },
  data() {
    const keys = Object.keys(this.sections)
    const index = keys.indexOf(this.current)

    return {
      startAngle: index > -1
        ? index * (360 / keys.length)
        : 0,
    }
  },
  methods: {
    angle(key) {
      const keys = Object.keys(this.sections)
      const index = keys.indexOf(key)

      return index * (360 / keys.length) - this.startAngle
    },
  },
  components: {
    RotorItem,
  },
  watch: {
    current(value) {
      const keys = Object.keys(this.sections)
      const index = keys.indexOf(value)

      const startAngle = index > -1
        ? index * (360 / keys.length)
        : 0

      const angleDif = this.startAngle % 360 - startAngle

      this.startAngle -= Math.abs(angleDif) > 180
        ? reverse(angleDif)
        : angleDif
    },
  },
}
</script>

<style lang="scss" scoped>
  .rotor {
    width: 500px;
    height: 500px;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .stator {
    width: 400px;
    height: 400px;
    border-radius: 50%;
    box-sizing: border-box;
    border: solid 1px rgba(164, 196, 255, .3);
  }
</style>
