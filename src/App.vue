<script >
import videoVue from './components/video.vue';
import Odot from './components/odot.vue';

export default {
  data() {
      return {
        page: "start", 
      };
  },
  methods: {
    insertedName() {
      document.getElementById("beginLesson").disabled = false;
    }
  },
  components: { Odot, videoVue }
  };
</script>

<template>
  <div id="app">
    <div class="openingPage" v-if="page==='start'">
      <img src="@/assets/images/odot2.svg" alt="odot" id="icon" @click="page='odot'" />
      <div class="boardAndButton">
        <div class="container playAnimation" id="board">
          <div id="openingTitle" class="playAnimationOnText">
          טכניקות מסירה
          </div>
          <div class="intoduction">
            <div id="question">איך קוראים לך?</div>
            <input type="input" id="nameInput" placeholder="שם מלא" @input="insertedName" />
          </div>
        </div>
        <button id="beginLesson" @click="page = 'video'" disabled="true">יאללה שנתחיל</button>
      </div>
    </div>
    <videoVue v-else-if="page==='video'"></videoVue>
    <Odot v-else-if="page==='odot'" @goBack="page='start'"></Odot>
  </div>
</template>

<style scoped>
@font-face {
  font-family: "heebo";
  src: url("@/assets/Heebo/Heebo-VariableFont_wght.ttf");
}

body {
  margin: 0;
  height: 60%;
  width: 100%;
}

#app {
  background-image: url("@/assets/images/background.png");
  background-repeat: no-repeat;
  background-size: cover;
  font-family: "heebo";
  user-select: none;
  overflow: hidden;
}

.playAnimation {
  animation: biggerBoard 1s 1s linear forwards;
  -webkit-animation: biggerBoard 1s 1s linear forwards;
}

.playAnimationOnText {
  animation: smallerText 1s 1s linear forwards;
  -webkit-animation: smallerText 1s 1s linear forwards;
}

.boardAndButton {
  display: flex;
  flex-direction: column;
  position: relative;
  top: 8.5vh;
  align-items: center;
}

.container {
  background-image: url("@/assets/images/board.png");
  background-size: 100% 100%;
  background-repeat: no-repeat;
  height: 45vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#openingTitle {
  margin-top: 7vh;
  font-size: 17vw;
  line-height: 9vh;
  text-align: center;
  direction: rtl;
  font-weight: 700;
}

.intoduction {
  margin-top: 2vh;
}

#beginLesson {
  width: 45vw;
  height: 10vh;
  border-style: none;
  padding-bottom: 1vh;
  color: white;
  background-color: transparent;
  font-size: 6vw;
  position: relative;
  top: 20.5vh;
  font-family: "heebo";
  background-image: url("@/assets/images/continueButton.png");
  background-size: 100% 100%;
}

#question {
  font-size: larger;
  direction: rtl;
}

#nameInput {
  text-align: right;
  border-style: none;
  width: 48vw;
  height: 3.5vh;
  border-radius: 2vw;
  background-color: rgba(128, 128, 128, 0.568);
}

.openingPage {
  display: flex;
  height: 100vh;
  width: 100%;
  flex-direction: column;
  flex-wrap: nowrap;
  align-items: center;
}

#icon {
  width: 7vw;
  height: 4vh;
  position: relative;
  left: 45vw;
  top: 1vh;
}

@keyframes biggerBoard {
  100% {
    background-size: 150% 100%;
  }
}

@-webkit-keyframes biggerBoard {
  100% {
    background-size: 150% 100%;
  }
}

@keyframes smallerText {
  0% {
    width: 100vw;
    font-size: 17vw;
  }
  100% {
    width: 70vw;
    font-size: 20vw;
  }
}

@-webkit-keyframes smallerText {
  0% {
    width: 100vw;
    font-size: 17vw;
  }
  100% {
    width: 70vw;
    font-size: 20vw;
  }
}
</style>
