<template lang="pug">
  v-layout(row text-xs-center)
    v-flex(xs4)
      panel(title="Song Metadata")
        v-text-field(label="Title" v-model="song.title")
        v-text-field(label="Artist" v-model="song.artist")
        v-text-field(label="Genre" v-model="song.genre")
        v-text-field(label="Album" v-model="song.album")
        v-text-field(label="Album Image Url" v-model="song.albumImageUrl")
        v-text-field(label="YouTube Id" v-model="song.youtubeId")
    v-flex(xs8).ml-2
      panel(title="Song Structure")
        v-text-field(label="Lyrics" multi-line v-model="song.lyrics")
        v-text-field(label="Tabs" multi-line v-model="song.tab")
        v-btn.cyan(@click="createSong" dark) Create
</template>

<script>
import Panel from '@/components/Panel'
import SongsService from '@/services/SongsService'

export default {
  data () {
    return {
      song: {
        title: null,
        artist: null,
        genre: null,
        album: null,
        albumImageUrl: null,
        youtubeId: null,
        lyrics: null,
        tab: null
      }
    }
  },
  methods: {
    async createSong () {
      try {
        console.log(this.song)
        await SongsService.post(this.song)
      } catch (error) {
        console.log(error)
      }
    }
  },
  components: {
    Panel
  }
}
</script>
