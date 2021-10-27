<template>
  <div id="reader_main">
    <div id="word-area" v-if="wordsEntered">
      <h1 id="word">
        {{word}}
      </h1>
      <p id="speed">
        {{speed}} WPM
      </p>
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
    msg: String
  }
})
export default class Reader extends Vue {
  wordsEntered = false
  enteredtext = ``
  read(): void {
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
h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}
#textentry {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
#reader-main {
  margin: 0;
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
}
textarea {
  width: 75%;
  height: 75%;
  resize: none;
}
button {
  padding: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
  background-color: white;
  border: solid 2px black;
  border-radius: 10px;
  margin: 10px;
  cursor: pointer;
}
</style>
