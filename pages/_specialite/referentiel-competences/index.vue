<template>
  <div class="container">
    <div>
      <h1 class="title">
        Référentiel Compétences de {{ sigle }}
      </h1>
      <b-tabs content-class="mt-3">
        <b-tab v-for="(comp, index) in competences.body.referentiel_competence.competences[0].competence" :key="index" :title="comp.$.name">
          <Competence :competence="comp" :couleur="comp.$.couleur" />
        </b-tab>
      </b-tabs>
      <NuxtLink :to="`/`+specialite.sigle">
        Retour
      </NuxtLink>
    </div>
  </div>
</template>

<script>
import conf from '../../../conf'
import Competence from '../../../components/Competence'

export default {
  components: { Competence },
  async asyncData ({ params, $content }) {
    const specialites = await $content(conf.SPECIALITES).fetch()
    const competences = await $content(conf.REFERENTIEL_COMPETENCES + params.specialite).fetch()
    return { specialites, competences }
  },
  data () {
    return {
      sigle: '',
      specialite: {},
      specialites: {}
    }
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
