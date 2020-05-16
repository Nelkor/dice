<template>
  <div class="main">
    <Rotor
      :sections="$options['sections']"
      :current="currentSection"
      origin="/"
    />

    <component :is="currentSection"/>
  </div>
</template>

<script>
import Rotor from '@/components/main/Rotor'

import News from '@/components/main/sections/News'
import Gains from '@/components/main/sections/Gains'
import Projects from '@/components/main/sections/Projects'
import Stories from '@/components/main/sections/Stories'
import Training from '@/components/main/sections/Training'

export default {
  name: 'Main',
  sections: {
    news: 'Новости',
    gains: 'Навыки',
    projects: 'Проекты',
    stories: 'Истории',
    training: 'Обучение',
  },
  computed: {
    paramSection() {
      return this.$route.params.section
    },
    currentSection() {
      const section = this.paramSection ? this.paramSection : 'news'

      return Object.keys(this.$options.sections).includes(section)
        ? section
        : null
    },
  },
  components: {
    Rotor,
    News,
    Gains,
    Projects,
    Stories,
    Training,
  },
  watch: {
    currentSection: {
      handler(value) {
        if (!value) return this.$router.replace('/')

        document.title = 'Dice — ' + this.$options.sections[value]
      },
      immediate: true,
    },
  },
}
</script>

<style lang="scss" scoped>
  .main {
    margin-top: 64px;
    display: flex;
    justify-content: center;
  }
</style>
