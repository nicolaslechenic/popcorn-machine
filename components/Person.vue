<template>
  <div class="person container section">
    <div class="columns">
      <div class="column">
        <PhotoCard :imageUrl="person.photo"/>
      </div>
      <div class="column is-two-thirds">
        <div class="columns">
          <div class="column is-two-thirds">
            <h1 style="text-transform:uppercase" class="title">{{person.prenom}} {{person.nom}}</h1>
            <h2 class="subtitle">{{person.titre}}</h2>
            <h2 class="subtitle">
              <Tags class="domaines-metiers" :tags="person.domaines_metiers"/>
            </h2>
            <h2 class="subtitle">
              <Tags class="technologies" :tags="person.technologies"/>
            </h2>
          </div>
          <div class="column">
            <button class="button is-primary" @click="showModal = true">
              <img style="width:20px; padding-right: 5px" src="/icons/envelope.svg">
              <span>Proposer un projet</span>
            </button>
          </div>
        </div>

        <div class="content" v-html="person.$html"></div>
      </div>
    </div>

    <div v-if="showModal" class="modal" :class="{'is-active': showModal}">
      <div class="modal-background" @click="showModal = false"></div>
      <div class="modal-content has-text-centered">
        <div class="box">
          <h1 class="title">Contacter {{person.prenom}} {{person.nom}}</h1>
          <h2 class="subtitle">{{person.titre}}</h2>
          <p style="margin-top:1rem" class="is-size-5">{{person.mail}}</p>
          <p
            v-show="person.telephone"
            style="margin-top:1rem"
            class="is-size-5"
          >{{person.telephone}}</p>
          <p style="margin-top:2rem">
            <em>Indiquez-lui que vous l'avez trouvé·e sur Popcorn :)</em>
          </p>
          <div style="font-size:3rem">🍿</div>
        </div>
        <!-- Any other Bulma elements you want -->
      </div>
      <button @click="showModal = false" class="modal-close is-large" aria-label="fermer"></button>
    </div>
  </div>
</template>

<script>
import Tags from './Tags'
import PhotoCard from './PhotoCard'

export default {
  components: {
    Tags,
    PhotoCard
  },
  props: {
    person: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      showModal: false
    }
  }
}
</script>
