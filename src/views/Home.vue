<template>
  <div id="id">
    <main>
      <section class="player">
        <h2 class="song-title">{{current.title}} - <span>{{ current.artist}}</span></h2>
        <div class="controls">
          <button class="prev" @click="prev">Prev</button>
          <button class="play" v-if="!isPlaying" @click="play">Play</button>
          <button class="pause" v-else @click="pause">Pause</button>
          <button class="next" @click="next">Next</button>
        </div>
      </section>
      <section class="playlist">
        <h3>The Playlist</h3>
        <button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' : 'song'">
          {{song.title}} - {{song.artist}}
        </button>
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
          src: require('../assets/Blaq_Diamond_-_Memeza_feat_Sjava.mp3')
        },
        {
          title: 'Ungbulalelani',
          artist: 'Blaq Diamond',
          src: require('../assets/Blaq_Diamond_-_Ung_bulalelani.mp3')
        },
        {
          title: 'Woza My Love',
          artist: 'Blaq Diamond',
          src: require('../assets/Blaq_Diamond_-_Woza_my_Love.mp3')
        },
        {
          title: 'PS',
          artist: 'Blaq Diamond',
          src: require('../assets/Blaq_Diamond_-_P_S.mp3')
        }
      ],
      player: new Audio()
    }
  },
  methods: {
    play(song) {
      if(typeof song.src != "undefined"){
        this.current = song
        this.player.src = this.current.src
      }
      this.player.play()
      this.player.addEventListener('ended', function () {
        this.index++
      if(this.index > this.songs.length - 1){
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
      }.bind(this));
      this.isPlaying = true
    },
    pause() {
      this.player.pause()
      this.isPlaying = false
    },
    next(){
      this.index++
      if(this.index > this.songs.length - 1){
        this.index = 0
      }
      this.current = this.songs[this.index]
      this.play(this.current)
    },
    prev() {
      this.index--
      if(this.index < 0){
        this.index = this.songs.length - 1
      }
      this.current = this.songs[this.index]
      this.play(this.current)
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

  main {
    width: 100%;
    margin: 0 auto;
    padding: 2rem;
  }

  .song-title {
    color: #212121;
    font-size: 2.5rem;
    text-transform: uppercase;
    text-align: center;
  }

  .song-title span {
    font-weight: lighter;
    font-style: italic;
  }

  .controls {
    display: flex;
    justify-content: center;
    padding: 30px 15px;
    align-items: center;
  }

  button {
    appearance: none;
    border: none;
    cursor: pointer;
    outline: none;
    background: none;
  }

  button:hover {
    opacity: 0.8;
  }

  .play, .pause {
    font-size: 1.5rem;
    font-weight: 700;
    padding: 1rem 1.5rem;
    color: #fff;
    background-color: #190061;
    border-radius: .7rem;
    margin: 0 1.5rem;
  }

  .next, .prev {
    font-size: 1rem;
    font-weight: 700;
    padding: 1rem 1.5rem;
    color: #fff;
    background-color: #240090;
    border-radius: .5rem;
    margin: 0 1rem;
  }

  .playlist {
    padding: 0 2rem;
  }

  .playlist h3 {
    color: #212121;
    font-size: 2rem;
    text-align: center;
    font-weight: 400;
    margin-bottom: 1.3rem;
  }

  .playlist .song {
    display: block;
    width: 100%;
    font-size: .9rem;
    font-weight: 600;
    padding: 1rem;
    cursor: pointer;
  }

  .playlist .song:hover {
    color: #3500d3;
  }

  .playlist .song.playing {
    color: #fff;
    background-image: linear-gradient(to right, #190061, #3500d3);
  }
</style>
