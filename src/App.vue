<template>
  <div id="id">
    <header>
      <h1>My Music</h1>
    </header>

    <main>
      <section class="player">
        <h2 class="song-title">{{current.title}} - <span>{{ current.artist}}</span></h2>
        <div class="controls">
          <button class="prev">Prev</button>
          <button class="play" v-if="!isPlaying">Play</button>
          <button class="pause" v-else>Pause</button>
          <button class="next">Next</button>
        </div>
      </section>
    </main>
  </div>
</template>

<script>


export default {
  name: 'App',
  data (){
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          title: 'Memeza',
          artist: 'Blaq Diamond',
          src: require('./assets/Blaq_Diamond_-_Memeza_feat_Sjava.mp3')
        },
        {
          title: 'Ungbulalelani',
          artist: 'Blaq Diamond',
          src: require('./assets/Blaq_Diamond_-_Ung_bulalelani.mp3')
        },
        {
          title: 'Woza My Love',
          artist: 'Blaq Diamond',
          src: require('./assets/Blaq_Diamond_-_Woza_my_Love.mp3')
        },
        {
          title: 'PS',
          artist: 'Blaq Diamond',
          src: require('./assets/Blaq_Diamond_-_P_S.mp3')
        }
      ],
      player: new Audio()
    }
  },
  created() {
    this.current = this.songs[this.index]
    this.player.src = this.current.src
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: sans-serif;
  }

  header {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
    background-color: #212121;
    color: #fff;
  }
</style>
