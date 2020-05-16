<template>
  <router-link
    class="rotor-item"
    :to="to"
    :style="{ transform }"
  >
    <div
      class="inner-item"
      :class="{ active }"
    >{{ text }}</div>
  </router-link>
</template>

<script>
export default {
  name: 'RotorItem',
  props: {
    text: String,
    active: Boolean,
    angle: Number,
    to: String,
  },
  computed: {
    transform() {
      return [
        `rotate(${-this.angle}deg)`,
        `translate(200px)`,
        `rotate(${this.angle}deg)`,
      ].join(' ')
    },
  },
}
</script>

<style lang="scss" scoped>
  .rotor-item {
    position: absolute;
    left: 190px;
    top: 190px;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 120px;
    height: 120px;
    text-decoration: none;
    color: inherit;
    transition: 1s;
  }

  .inner-item {
    box-shadow: 0 2px 8px rgba(79, 94, 105, .24);
    background: #fff;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    transform: scale(.7);
    opacity: .8;
    transition: inherit;

    &:hover {
      color: #3874e0;
      transform: scale(.8);
      opacity: .9;
    }

    &.active {
      transform: scale(1);
      opacity: 1;
      color: #3874e0;
    }
  }
</style>
