<template>
  <div>
    <div class="d-flex align-items-stretch mt-3">
      <div class="col-3 competence">
        <div :class="`p-3 comp competence ${couleur}`">{{ competence.$.name }}</div>
      </div>
      <div class="col-3 competencelongue  ms-3">
        <div :class="`p-3 competencelongue${couleur}`">{{ competence.$.libelle_long }}
        </div>
      </div>
      <div :class="`col-6 composantesessentielles${couleur}`">
        <div>
          <ul>
            <li  v-for=" (composante_essentielle, index) in competence.composantes_essentielles[0].composante" :key="index">
              {{ composante_essentielle }}
            </li>
          </ul>
        </div>
      </div>
    </div>

    <div class="d-flex align-items-stretch mt-3">
      <div class="col-3">
        <div :class="`p-3 situationpro situation${couleur}`">Situations professionnelles</div>
      </div>
      <div class="col-9  ms-3">
        <div :class="`p-3 situationliste${couleur}`">
          <ul>
            <li v-for=" (situation, index) in competence.situations[0].situation" :key="index">{{ situation }}</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="d-flex align-items-stretch mt-3">
      <div class="col-3">
        <div class="p-3 titreniveau">
          Niveaux
        </div>
      </div>
      <div class="col-9 ms-3 ">
        <div class="p-3 titreac">
          Apprentissages critiques
        </div>
      </div>
    </div>

    <div class="d-flex align-items-stretch mt-3" v-for="(niveau, index) in competence.niveaux[0].niveau" :key="index">
      <div :class="`col-3 niveau  niveau${niveau.$.ordre}${couleur}`">
        <div class="p-3 niveaucourt ">
          Novice B.U.T. {{ niveau.$.ordre }}
        </div>
        <div class="p-3 niveaulong">
          {{ niveau.$.libelle }}
        </div>
      </div>
      <div class="col-9 ms-3 ">
        <div :class="`p-3 niveauliste niveau1${couleur}`">
          <ul>
            <li v-for="(ac, indexac) in niveau.acs[0].ac" :key="indexac">
              {{ ac.$.code}} : {{ ac._}}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Competence',
  props: {
    competence: {},
    couleur: String
  }
}
</script>

<style scoped>

</style>
