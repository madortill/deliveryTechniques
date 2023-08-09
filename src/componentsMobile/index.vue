<script >
import videoVue from './video.vue';
import Odot from './odot.vue';

export default {
  data() {
      return {
        page: "start", 
        isloaded: false
      };
  },
  methods: {
    insertedName() {
      document.getElementById("beginLesson").classList.remove("disabled");
      document.getElementById("beginLesson").classList.add("abled");
      document.getElementById("beginLesson").disabled = false;
    }
  },
  mounted() {
    document.onreadystatechange = () => {
      if (document.readyState == "complete") {
        this.$refs.loader.classList.add("fade");
        this.isloaded = true;
      }
    }
  },
  components: { Odot, videoVue }
  };
</script>

<template>
  <div id="index">
    <div class="loader" ref="loader" v-if="!isloaded">
        <img src="/center and mask.gif" alt="Loading..." />
        מייד מתחילים...
    </div>
    <div class="openingPage" v-if="page==='start'">
      <img src="@/assets/images/odot2.svg" alt="odot" id="icon" @click="page='odot'" />
      <div class="boardAndButton">
        <div class="container" id="board">
          <div id="openingTitle">
          טכניקות מסירה
          </div>
          <div class="intoduction">
            <div id="question">איך קוראים לך?</div>
            <input type="input" id="nameInput" placeholder="שם מלא" @input="insertedName" />
          </div>
        </div>
        <button id="beginLesson" @click="page = 'video'" disabled="true" class="disabled">יאללה שנתחיל</button>
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
  height: 80vh;
  width: 100vw;
  overflow: hidden;
}
.loader {
    position: fixed;
    z-index: 99;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: #f4f4f4;
    display: flex;
    direction: rtl;
    justify-content: center;
    align-items: center;
    color: #79BEE0;
    font-size: 2em;
    font-weight: 800;
}

.loader > img {
    width: 50vw;
}

.loader.fade {
    animation: fadeOut 1s 2s forwards;
}

@keyframes fadeOut {
    100% {
        opacity: 0;
        visibility: hidden;
    }
}

#index {
  height: 100%;
  width: 100%;
  background-image: url("@/assets/images/background.png");
  background-repeat: no-repeat;
  background-size: cover;
  font-family: "heebo";
  user-select: none;
  overflow: hidden;
  position: fixed;
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
  transform: scale(1.15, 1.15);
  background-repeat: no-repeat;
  height: 45vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#openingTitle {
  margin-top: 7vh;
  font-size: 18vw;
  line-height: 9vh;
  text-align: center;
  direction: rtl;
  font-weight: 600;
}

.intoduction {
  margin-top: 2vh;
}

.abled {
  filter: grayscale(0%);
}
.disabled {
  filter: grayscale(60%);
}

#beginLesson {
  width: 50vw;
  height: 10.5vh;
  border-style: none;
  padding-bottom: 1vh;
  color: white;
  background-color: transparent;
  font-size: 6vw;
  position: absolute;
  top: 66vh;
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

</style>
