<script>
import ExplanationPage from './explanationPage.vue';

export default {
  data() {
    return {
      nextPage: "video"
    };
  },
  methods: {
    showPage() {
      this.nextPage = 'video';
    }
  },
  components: { ExplanationPage }
  };
</script>

<template>
  <div id="video">
    <div v-if="nextPage === 'video'" class="container">
      <div class="board playAnimation">
        <iframe src="https://www.youtube.com/embed/kRIV8_lgpfU" title="YouTube video player" frameborder="0" class="speakingVideo" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
      </div>
      <button id="toExplanation" @click="nextPage = 'explain'" class="playAnimationOnButton">לתקציר</button>
    </div>
    <ExplanationPage v-else @backPage="showPage"></ExplanationPage>
  </div>
</template>

<style scoped>

.speakingVideo {
  width: 85vw;
  height: 35vh;
  padding-top: 4vh;
  padding-bottom: 7vh;
}

@keyframes smaller {
  100% {
    transform: scale(1, 1);
  }
}

@-webkit-keyframes smaller {
  100% {
    transform: scale(1, 1);
  }
}

.playAnimation {
  animation: smaller 1s ease-out forwards;
  -webkit-animation: smaller 1s ease-out forwards;
}

#toExplanation {
  width: 49vw;
  height: 10vh;
  padding-bottom: 1vh;
  border-style: none;
  background-color: transparent;
  font-size: 2.5vmax;
  position: absolute;
  top: 66vh;
  background-image: url("@/assets/images/continueButton.png");
  background-size: 100% 100%;
  font-family: "heebo";
  color: white;
}

.container {
  position: relative;
  top: 12vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.board {
  background-image: url("@/assets/images/board.png");
  background-size: 100% 100%;
  display: flex;
  width: 107vw;
  transform: scale(1.15, 1.15);
  justify-content: center;
}

@keyframes smallerButton {
  100% {
    width: 42vw;
    height: 7vh;
    position: absolute;
    top: 70vh;
  }
}

@-webkit-keyframes smallerButton {
  100% {
    width: 42vw;
    height: 7vh;
    position: absolute;
    top: 70vh;
  }
}

.playAnimationOnButton{
  animation: smallerButton 1s ease-out forwards;
  -webkit-animation: smallerButton 1s ease-out forwards;
}
</style> 
