<template>
  <div class="container">
    <div>
      <h1 class="title">
        Homepage de {{ sigle }}
      </h1>

      <NuxtLink :to="`/`+specialite.sigle+`/referentiel-competences`">
        Référentiel de compétences
      </NuxtLink>
      <NuxtLink :to="`/`+specialite.sigle+`/referentiel-formation`">
        Référentiel de formation
      </NuxtLink>
      <NuxtLink to="/">
        Retour
      </NuxtLink>
    </div>
  </div>
</template>

<script>
import conf from '../../conf'

export default {
  data () {
    return {
      sigle: '',
      specialite: {},
      specialites: {}
    }
  },
  async asyncData ({ $content }) {
    const specialites = await $content(conf.SPECIALITES).fetch()
    return { specialites }
  },
  mounted () {
    this.sigle = this.$route.params.specialite
    this.specialite = this.specialites[this.$route.params.specialite]
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
