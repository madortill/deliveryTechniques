<script >
import ExplanationPage from './explanationPage.vue';

export default {
  data() {
      return {
        nextPage: "video"
      };
  },
  methods: {
      
  },
  components: { ExplanationPage }
  };
</script>

<template>
  <div id="video">
    <div v-if="nextPage === 'video'" class="container">
      <div class="board">
        <iframe src="https://www.youtube.com/embed/kRIV8_lgpfU" title="YouTube video player" frameborder="0" class="speakingVideo" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
      </div>
      <button id="toExplanation" @click="nextPage = 'explain'">לתקציר</button>
    </div>
    <ExplanationPage v-else></ExplanationPage>
  </div>
</template>

<style scoped>

.speakingVideo {
  width: 85vw;
  height: 35vh;
  padding-top: 4vh;
  padding-bottom: 7vh;
}

#toExplanation {
  width: 42vw;
  height: 7vh;
  padding-bottom: 1vh;
  border-style: none;
  background-color: transparent;
  font-size: 5.5vw;
  position: relative;
  top: 27vh;
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
  justify-content: center;
}
</style> 
