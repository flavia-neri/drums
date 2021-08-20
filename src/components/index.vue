<template>
  <section class="drum-container">
    <h1>BATERIA</h1>
    <div class="keys">
      <div class="key" v-for="key in keys" :key="key" :data-key="key.id">
        {{ key.letter }}
      </div>
    </div>
    <div class="composition-container">
      <form>
        <input type="text" placeholder="Faça uma composição aqui..." />
        <button>TOCAR</button>
      </form>
    </div>
    <h5>Flávia Neri</h5>

    <audio
      v-for="audio in audios"
      :key="audio.id"
      :id="audio.id"
      :src="audio.src"
    >
    </audio>
  </section>
</template>

<script>
document.title = "Bateria";
export default {
  data: function() {
    return {
      keys: [
        { letter: "Q", id: "keyq" },
        { letter: "W", id: "keyw" },
        { letter: "E", id: "keye" },
        { letter: "A", id: "keya" },
        { letter: "S", id: "keys" },
        { letter: "D", id: "keyd" },
        { letter: "Z", id: "keyz" },
        { letter: "X", id: "keyx" },
        { letter: "C", id: "keyc" },
      ],
      audios: [
        { id: "keyq", src: require("../assets/sounds/keyq.wav") },
        { id: "keyw", src: require("../assets/sounds/keyw.wav")},
        { id: "keye", src: require("../assets/sounds/keye.wav") },
        { id: "keya", src: require("../assets/sounds/keya.wav") },
        { id: "keys", src: require("../assets/sounds/keys.wav") },
        { id: "keyd", src: require("../assets/sounds/keyd.wav") },
        { id: "keyz", src: require("../assets/sounds/keyz.wav") },
        { id: "keyx", src: require("../assets/sounds/keyx.wav") },
        { id: "keyc", src: require("../assets/sounds/keyc.wav") },
      ],
    };
  },
  created: function(){
      window.addEventListener('keyup', this.keyup);
  },
  methods: {
      keyup(event){
          this.playSound(event.code.toLowerCase());
      },
      playSound(sound){
           let audioElement = document.querySelector(`#${sound}`);
           let keyElement = document.querySelector(`div[data-key='${sound}']`);
           if(audioElement){
             audioElement.currentTime = 0;
             audioElement.play();
            }
            if(keyElement){
              keyElement.classList.add("active");

              setTimeout(() => {
                keyElement.classList.remove("active");
              }, 200)
            }
      }
  },
};
</script>
<style lang="scss">
@font-face {
  font-family: "Fritlany";
  src: url("../assets/Fritlany.ttf");
}
.drum-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #161616;
  h1 {
    margin: 0;
    padding: 0;
    font-size: 34px;
    color: #c9c9c9;
    letter-spacing: 3px;
  }
  .keys {
    margin: 30px 0;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1em;
    .key {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100px;
      height: 100px;
      border-radius: 10px;
      border: 1px solid #fff;
      color: #c9c9c9;
      font-size: 30px;
      cursor: pointer;
      &:hover {
        background-color: rgba(48, 48, 48, 0.2);
      }
    }
    .active {
      background-color: rgba(48, 48, 48, 0.2);
      transform: scale(1.1);
    }
  }
  .composition-container {
    form {
      display: flex;
      flex-direction: column;
      input,
      button {
        width: 320px;
        height: 40px;
        padding-left: 10px;
        color: #c9c9c9;
        font-size: 20px;
        border: 1px solid #fff;
        border-radius: 5px;
        background-color: transparent;
        text-transform: uppercase;

        &::placeholder {
          font-size: 16px;
          text-transform: none;
        }
      }
      button {
        margin-top: 15px;
        cursor: pointer;
        &:hover {
          background-color: rgba(48, 48, 48, 0.2);
        }
        &:active {
          transform: scale(1.01);
        }
      }
    }
  }
  h5 {
    color: #c9c9c9;
    font-family: Fritlany;
  }
}
</style>
