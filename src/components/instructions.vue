<script>
import Exercize from './exercize.vue';

export default {
    data() {
        return {
            nextPage: false
        }
    },
    methods: {
        backPage() {
            this.$emit('prevPage');
        }
    },
    components: { Exercize }

};

</script>

<template>
    <div id="instrctions">
        <div v-if="nextPage === false" class="page">
            <div class="board playAnimationOnBoard">
                <div class="text">
                    המפקדת מאחרת לשיעור אבל היא לא מדוגמת ולא מוכנה לעמוד מול הקהל. כאן התפקיד שלכם נכנס לתמונה: תענו על השאלות נכון וכך תוכלו לעזור לה להתכונן לשיעור. 
                </div>
                <div class="buttonCont">
                    <button class="continue" type="button" @click="nextPage = true">אעזור לה!</button>
                    <button class="back" type="button" @click="backPage">חזרה על החומר</button>
                </div>
            </div>
            <img src="@/assets/images/table.png" alt="table" class="table" />
        </div>
        <Exercize v-else></Exercize>
    </div>
</template>



<style scoped>
#instrctions {
    height: 100%;
}

.text {
    text-align: center;
    /* padding-top: 4vh; */
    font-size: 2vh;
    width: 25vw;
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

.playAnimation {
  animation: higherBoard 1s ease-out forwards;
  -webkit-animation: higherBoard 1s ease-out forwards;
}

.buttonCont {
    display: flex;
    flex-direction: row-reverse;
    width: 20vw;
    justify-content: space-between;
}
.board {
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    transform: scale(1.75, 1.75);
    background-repeat: no-repeat;
    height: 30vh;
    width: 30vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    justify-content: center;
}

.back {
    width: 8vw;
    height: 5vh;
    border-style: none;
    padding-bottom: 1vh;
    color: white;
    background-color: transparent;
    font-size: 1.7vh;
    font-family: "heebo";
    background-image: url("@/assets/images/continueButton.png");
    background-size: 100% 100%;
}
.continue {
    width: 8vw;
    height: 5vh;
    border-style: none;
    padding-bottom: 1vh;
    color: white;
    background-color: transparent;
    font-size: 1.7vh;
    font-family: "heebo";
    background-image: url("@/assets/images/continueButton.png");
    background-size: 100% 100%;
}

.page {
    display: flex;
    height: 100%;
    flex-direction: column;
    align-items: center;
    direction: rtl;
    margin-top: 7vh;
    justify-content: space-around;
}

.table {
    width: 40vw;
    height: 30vh;
}
</style>