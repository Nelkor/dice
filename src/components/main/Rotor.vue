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

export default {
  name: 'Rotor',
  props: {
    sections: Object,
    current: String,
    origin: String,
  },
  computed: {
    startAngle() {
      if (!this.current) return 0

      const keys = Object.keys(this.sections)
      const index = keys.indexOf(this.current)

      return index * (360 / keys.length)
    },
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
