<template>
  <div class="home">
    <transition name="fade">
      <Loading v-if="loading" :total="sounds.length" :loaded="loaded"/>
    </transition>
    <div class="page">
      <h1 class="title">Kadir-B<img src="./../assets/vlad-rounded.png" alt="O" height="25px">X</h1>
      <div class="sounds">
        <div class="sound" v-for="(sound, index) in sounds" :key="index">
          <div class="sound-box" :class="{ play: sound.play }">
            <span class="id">{{ index + 1 }}</span>
            <div class="name">{{ sound.name }}</div>
            <button class="button" @click="play(sound.audio, index); sound.play">Play !</button>
          </div>
        </div>
      </div>
      <div class="footer">
        <span>
          Fait avec 
          <svg fill="white" version="1.1" id="love" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="13px" height="13px" viewBox="0 0 510 510" ><path d="M255,489.6l-35.7-35.7C86.7,336.6,0,257.55,0,160.65C0,81.6,61.2,20.4,140.25,20.4c43.35,0,86.7,20.4,114.75,53.55 C283.05,40.8,326.4,20.4,369.75,20.4C448.8,20.4,510,81.6,510,160.65c0,96.9-86.7,175.95-219.3,293.25L255,489.6z"/></svg>
          par&nbsp;<span class="bold">Gatien Anizan</span>&nbsp;en un week-end.
        </span><br>
        <span><a style="color: white;" href="https://github.com/mrpinkcat" target="blank">GitHub</a> - <a style="color: white;" href="https://mrpink.dev" target="blank">Website</a></span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Loading from '@/components/Loading.vue'; // @ is an alias to /src

@Component({
  components: {
    Loading,
  },
})
export default class Home extends Vue {
  public loading: boolean = true;
  public sounds: Array<{ name: string, src: NodeRequire, play: boolean, audio: HTMLAudioElement | undefined }> = [
    { name: 'Ok', src: require('./../sounds/ok1.mp3'), play: false, audio: undefined },
    { name: 'Ok (expiration)', src: require('./../sounds/ok2.mp3'), play: false, audio: undefined },
    { name: 'Homme intégrallement nue', src: require('./../sounds/homme-integralement-nue.mp3'), play: false, audio: undefined },
    { name: 'Gros viens enculé', src: require('./../sounds/gros-viens-encule.mp3'), play: false, audio: undefined },
    { name: 'Le sang de tes morts, viens', src: require('./../sounds/sang-de-tes-mort-viens.mp3'), play: false, audio: undefined },
    { name: 'Enculeur de mouche', src: require('./../sounds/enculeur-de-mouche.mp3'), play: false, audio: undefined },
    { name: 'Viens', src: require('./../sounds/viens.mp3'), play: false, audio: undefined },
    { name: 'Hé Ho', src: require('./../sounds/he-ho.mp3'), play: false, audio: undefined },
    { name: 'Hé ramenne toi', src: require('./../sounds/he-ramenne-toi.mp3'), play: false, audio: undefined },
    { name: 'Plus vite que ça', src: require('./../sounds/plus-vite-que-ca.mp3'), play: false, audio: undefined },
    { name: 'Bouge ton cul', src: require('./../sounds/bouge-ton-cul.mp3'), play: false, audio: undefined },
    { name: 'On a pas toute la nuit', src: require('./../sounds/on-a-pas-toute-la-nuit.mp3'), play: false, audio: undefined },
    { name: 'Allé', src: require('./../sounds/alle.mp3'), play: false, audio: undefined },
    { name: 'Vieeeeennnns', src: require('./../sounds/viens-insistant.mp3'), play: false, audio: undefined },
    { name: 'Viens !', src: require('./../sounds/viens-direct.mp3'), play: false, audio: undefined },
    { name: 'Viens stp ...', src: require('./../sounds/viens-stp-chuhcotement.mp3'), play: false, audio: undefined },
    { name: 'Viens x2', src: require('./../sounds/viens-x2.mp3'), play: false, audio: undefined },
    { name: 'Gatien', src: require('./../sounds/gatien-mistique.mp3'), play: false, audio: undefined },
    { name: 'Gatien ?', src: require('./../sounds/gatien-mistique-fache.mp3'), play: false, audio: undefined },
  ];
  public loaded: number = 0;

  public mounted() {
    this.sounds.forEach((sound) => {
      // @ts-ignore
      const audio = new Audio(sound.src);
      audio.addEventListener('canplaythrough', this.loadedAudio, false);
      sound.audio = audio;
    });
  }

  public loadedAudio() {
    this.loaded++;
    if (this.loaded === this.sounds.length) {
      this.loading = false;
    }
  }

  public play(audio: HTMLAudioElement, index: number) {
    audio.play();
    this.sounds[index].play = true;
    setTimeout(() => {
      this.sounds[index].play = false;
    }, audio.duration * 1000);
  }
}
</script>

<style lang="scss" scoped>
.home {
  height: 100%;
  .page {
    width: calc(100% - 60px);
    margin: 30px;
    .title {
      width: 100%;
      text-align: center;
    }
    .sounds {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      .sound {
        flex-basis: 20%;
        flex-grow: 1;

        display: flex;
        justify-content: center;
        .sound-box {
          display: flex;
          justify-content: center;
          align-items: center;
          flex-direction: column;
          width: 225px;
          margin: 16px;
          padding: 8px;
          border: 2px solid hsl(205, 25, 25);
          background: hsl(205, 25, 25);
          border-radius: 8px;
          &.play {
            border: 2px solid #1DBC60;
          }
          .name {
            font-weight: bold;
            margin: 4px 0;
            font-size: 18px;
            text-align: center;
          }
          .button {
            margin: 4px;
            height: 30px;
            width: 150px;
            background: #1DBC60;
            border: none;
            border-radius: 4px;
            color: white;
          } 
        }
      } 
    }
    .footer {
      margin: 30px 0;
      text-align: center;
      .bold {
        font-weight: bold;
      }
      #love {
        margin: 2px 2px 0 2px;
      }
    }
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>

