<template>
  <div id="reader_main">
    <div id="word-area" v-if="wordsEntered">
      <h1 id="word">
        {{word}}
      </h1>
      <input type="range" min="1" :max="words.length" v-model="wordIndex" id="word-slider" class="slider">
      <p v-if="!playing">Word {{wordIndex}} of {{words.length}}</p>
      <p id="speed">
        {{speed}} WPM
      </p>
      <p>{{timeElapsed}} / {{totalTime}}<br>{{timeLeft}} left</p>
      <button @click="edit()" id="back">Edit Text</button>
    </div>

    <div id="textentry" v-else>
      <textarea v-model="enteredtext" name="textarea" id="textarea"></textarea>
      <button @click="read()">Start Reading</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
  }
})
export default class Reader extends Vue {
  wordsEntered = false
  enteredtext = `Paste text here to read it quickly`

  read(): void {
    this.words = []
    let tempWords = this.enteredtext.split(/[\s\n]/)
    for (let i = 0; i < tempWords.length; i++) {
      if (/\w+/.test(tempWords[i])) {
        this.words.push(tempWords[i])
      }
    }
    this.wordsEntered = true
  }

  edit(): void {
    this.pause()
    this.wordsEntered = false
  }
  
  playing = false

  playLoop(): void {
    if (this.wordIndex >= this.words.length) {
      this.playing = false
      this.wordIndex = 0
    }
    if (this.playing) {
      this.wordIndex++
      setTimeout(this.playLoop, 1000/(this.speed/60))
    }
  }

  play(): void {
    this.playing = true
    this.playLoop()
  }

  pause(): void {
    this.playing = false
  }

  words: string[] = []
  wordIndex = 0
  get word(): string {
    return this.words[this.wordIndex]
  }

  speed = 600

  minSecs(seconds_in: number):string {
    let minutes = new String(Math.floor(seconds_in/60))
    let seconds = new String(Math.round(seconds_in - 60*Math.floor(seconds_in/60)))
    return minutes + ":" + (Number(seconds) < 10 ? "0" : "") + seconds
  }

  get timeElapsed(): string {
    let time = Math.round(this.wordIndex / (this.speed / 60))
    return this.minSecs(time) 
  }
  get totalTime(): string {
    let time = (this.words.length / (this.speed / 60))
    return this.minSecs(time)
  }
  get timeLeft(): string {
    let time = ((this.words.length - this.wordIndex) / (this.speed / 60))
    return this.minSecs(time)
  }

  mounted(): void {
    document.addEventListener('keydown', (e) => {
      switch (e.key) {
        case ("ArrowUp"):
          this.speed += 25
          break
        case ("ArrowDown"):
          this.speed -= 25
          break
        case ("ArrowLeft"):
          this.wordIndex--
          break
        case ("ArrowRight"):
          this.wordIndex++
          break
        case (" "):
          if (this.playing) {
            this.pause()
          }
          else {
            this.play()
          }
          break
        case ("r"):
          this.wordIndex = 0
          break
      }
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#reader-main {
  margin: 0;
}

h3 {
  margin: 40px 0 0;
}

#textentry {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

#word-area {
  display: flex;
  flex-direction: column;
  flex: 4 1 1;
  align-items: center;
  justify-content: center;
}

#word {
  margin-top: 10%;
  margin-bottom: 50px;
  font-size: 2.5rem;
}

#word-slider {
  margin-top: 10px;
  width: 50%;
}

textarea {
  width: 75%;
  height: 75%;
  resize: none;
  padding: 5px;
  border-radius: 5px;
  border-style: solid;
  border-width: 1px;
  background: var(--background-color-primary);
  color: var(--text-primary-color);
  transition: background-color var(--transition-time), color var(--transition-time);
}

textarea:focus {
  outline: none;
}

button {
  padding: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
  border: solid 1px;
  border-radius: 10px;
  margin: 10px;
  cursor: pointer;
}
.slider {
  -webkit-appearance: none;
  width: 100%;
  height: 10px;
  border-radius: 5px;
  background: var(--accent-color);
  outline: none;
  opacity: 0.7;
  -webkit-transition: .2s;
  transition: opacity .2s;
  transition: background-color var(--transition-time);
}

.slider:hover {
  opacity: 1;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 20px;
  height: 20px;
  background: var(--slider-color);
  cursor: pointer;
  border-radius: 10px;
  transition: background-color var(--transition-time);
}

.slider::-moz-range-thumb {
  width: 20px;
  height: 20px;
  background: var(--slider-color);
  cursor: pointer;
  border-radius: 10px;
  border: none;
  transition: background-color var(--transition-time);
}

</style>
