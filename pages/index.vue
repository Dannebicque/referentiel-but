<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        Référentiels de Compétences et de Formation des 24 spécialités de Bachelor Universitaire de Technologie (B.U.T.)
      </h1>
      <div>
        <div v-for="specialite in specialites" :key="specialite.sigle">
          <NuxtLink :to="`/`+specialite.sigle">
            {{ specialite.sigle }}
          </NuxtLink>
        </div>
      </div>
      <NuxtLink to="/about">
        A propos de ce site
      </NuxtLink>
    </div>
  </div>
</template>

<script>
import conf from '../conf'

export default {
  async asyncData ({ $content }) {
    const specialites = await $content(conf.SPECIALITES).fetch()
    return { specialites }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 100;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
