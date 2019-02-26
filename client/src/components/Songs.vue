<template lang="pug">
  panel(title="Songs")
    div(v-for="song in songs" :key="song.title") {{ song.title }}
</template>

<script>
import Panel from '@/components/Panel'
import SongsService from '@/services/SongsService'

export default {
  data () {
    return {
      songs: null
    }
  },
  async mounted () {
    this.songs = (await SongsService.index()).data
    console.log(this.songs)
  },
  components: {
    Panel
  }
}
</script>
