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
            <div class="board">
                <div class="text">
                    המפקדת מאחרת לשיעור אבל היא לא מדוגמת ולא מוכנה לעמוד מול הקהל. כאן התפקיד שלכם נכנס לתמונה: תענו על השאלות נכון וכך תוכלו לעזור לה להתכונן לשיעור. 
                </div>
                <div class="buttonCont">
                    <button class="continue" type="button" @click="nextPage = true">אעזור לה!</button>
                    <button class="back" type="button" @click="backPage">רגע רוצה לחזור על החומר</button>
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
    bottom: 7.5vh;
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
    font-size: 4.5vw;
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
    font-size: 5.5vw;
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