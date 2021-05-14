<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        Référentiels de Compétences et de Formation des 24 spécialités de Bachelor Universitaire de Technologie (B.U.T.)
      </h1>
      <div class="row">
        <div
          class="col-4"
          v-for="specialite in specialitesFiltre"
          :key="specialite.sigle"
        >
          <b-card
            :title="specialite.sigle"
            img-src="https://picsum.photos/600/300/?image=25"
            img-alt="Image"
            img-top
            style="max-width: 20rem;"
            class="mb-2"
          >
            <b-card-text>
              {{ specialite.libelle }}
            </b-card-text>

            <b-button :to="`/`+specialite.sigle" variant="primary">Voir les référentiels</b-button>
          </b-card>
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
  },
  computed: {
    specialitesFiltre () {
      delete this.specialites.slug
      delete this.specialites.dir
      delete this.specialites.path
      delete this.specialites.createdAt
      delete this.specialites.updatedAt
      delete this.specialites.extension
      return this.specialites
    }
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
