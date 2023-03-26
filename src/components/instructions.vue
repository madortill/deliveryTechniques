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
            <div class="board playAnimation">
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
.text {
    text-align: center;
    padding-top: 4vh;
    width: 85vw;
}

@keyframes higherBoard {
  100% {
    top: -7.5vh;
  }
}

@-webkit-keyframes higherBoard {
  100% {
    top: -7.5vh;
  }
}

.playAnimation {
  animation: higherBoard 1s ease-out forwards;
  -webkit-animation: higherBoard 1s ease-out forwards;
}

.buttonCont {
    display: flex;
    flex-direction: row-reverse;
    width: 80vw;
    justify-content: space-between;
}
.board {
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    height: 42vh;
    width: 108vw;
    position: relative;
    top: 30vh;
    z-index: 100;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.back {
    text-align: center;
    margin-top: 1vh;
    width: 36vw;
    height: 8vh;
    color: white;
    font-family: "heebo";
    font-size: 2.5vmax;
    background-image: url("@/assets/images/continueButton.png");
    background-color: transparent;
    border-style: none;
    background-size: 100% 100%;  
}
.continue {
    text-align: center;
    margin-top: 1vh;
    width: 36vw;
    height: 8vh;
    color: white;
    font-family: "heebo";
    font-size: 2.5vmax;
    background-image: url("@/assets/images/continueButton.png");
    background-color: transparent;
    border-style: none;
    background-size: 100% 100%;
}

.page {
    display: flex;
    flex-direction: column;
    align-items: center;
    direction: rtl;
    margin-top: 20vh;
}

.table {
    position: relative;
    bottom: 4vh;
    width: 100vw;
    height: 40vh;
}
</style>