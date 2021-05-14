<template>
  <div class="container">
    <div>
      <h1 class="title">
        B.U.T. {{ sigle }}
      </h1>
      <div class="row">
        <div
          class="col-4"
        >
          <b-card
            title="Référentiel de compétences"
            img-src="https://picsum.photos/600/300/?image=25"
            img-alt="Image"
            img-top
            style="max-width: 20rem;"
            class="mb-2"
          >
            <b-card-text>
              Voir le référentiel de compétences : niveaux, composantes essentielles, apprentissages critiques
            </b-card-text>

            <b-button :to="`/`+specialite.sigle+`/referentiel-competences`" variant="primary">Voir le référentiel</b-button>
          </b-card>
        </div>

        <div
          class="col-4"
        >
          <b-card
            title="Parcours"
            img-src="https://picsum.photos/600/300/?image=25"
            img-alt="Image"
            img-top
            style="max-width: 20rem;"
            class="mb-2"
          >
            <b-card-text>
              Voir les Parcours
            </b-card-text>

            <b-button :to="`/`+specialite.sigle+`/referentiel-competences`" variant="primary">Voir les parcours</b-button>
          </b-card>
        </div>

        <div
          class="col-4"
        >
          <b-card
            title="Référentiel de formation"
            img-src="https://picsum.photos/600/300/?image=25"
            img-alt="Image"
            img-top
            style="max-width: 20rem;"
            class="mb-2"
          >
            <b-card-text>
              Voir le référentiel de formation : Ressources, SAE, par semestre
            </b-card-text>
            <b-button :to="`/`+specialite.sigle+`/referentiel-formation`" variant="primary">Voir le référentiel</b-button>
          </b-card>
        </div>
      </div>
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
