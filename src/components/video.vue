<script>
import ExplanationPage from './explanationPage.vue';

export default {
  data() {
    return {
      nextPage: "video",
      cameFromBack: false

    };
  },
  methods: {
    showPage() {
      this.nextPage = 'video';
      this.cameFromBack = true;
    }
  },
  components: { ExplanationPage }
  };
</script>

<template>
  <div id="video">
    <div v-if="nextPage === 'video'" class="container">
      <div class="board" :class="cameFromBack ? 'playAnimationOnBoard' : ''">
        <iframe src="https://www.youtube.com/embed/kRIV8_lgpfU" title="YouTube video player" frameborder="0" class="speakingVideo" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
      </div>
      <button id="toExplanation" @click="nextPage = 'explain'" class="playAnimationOnButton">לתקציר</button>
    </div>
    <ExplanationPage v-else @backPage="showPage"></ExplanationPage>
  </div>
</template>

<style scoped>

#video {
  height: 100%;
}

.speakingVideo {
  width: 22vw;
  height: 21vh;
}

.playAnimation {
  animation: smaller 1s ease-out forwards;
  -webkit-animation: smaller 1s ease-out forwards;
}

#toExplanation {
  width: 20vw;
  height: 10.5vh;
  border-style: none;
  padding-bottom: 1vh;
  color: white;
  background-color: transparent;
  font-size: 2vmax;
  font-family: "heebo";
  background-image: url("@/assets/images/continueButton.png");
  background-size: 100% 100%;
}

.container {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
}

.board {
  background-image: url("@/assets/images/board.png");
  background-size: 100% 100%;
  transform: scale(1.75, 1.75);
  background-repeat: no-repeat;
  margin-top: 3vh;
  height: 30vh;
  width: 30vw;
  display: flex;
  flex-direction: column;
  position: relative;
  align-items: center;
  justify-content: center;
}

@keyframes higherBoard {
  0% {
    top: 20vh;
  }
  100% {
    top: 0vh;
  }
}

@-webkit-keyframes higherBoard {
  0% {
    top: 20vh;
  }
  100% {
    top: 0vh;
  }
}

.playAnimationOnBoard{
  animation: higherBoard 1s ease-out forwards;
  -webkit-animation: higherBoard 1s ease-out forwards;
}
</style> 
