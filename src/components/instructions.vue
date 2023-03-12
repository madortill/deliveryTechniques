<script>
import Exercize from './exercize.vue';

export default {
    data() {
        return {
            nextPage: false
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
                <button class="continue" type="button" @click="nextPage = true">אעזור לה!</button>
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
    width: 90vw;
}
.board {
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    height: 40vh;
    width: 108vw;
    position: relative;
    bottom: 7.5vh;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.continue {
    text-align: center;
    margin-top: 2vh;
    width: 38vw;
    height: 6vh;
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
    bottom: 2vh;
    width: 100vw;
    height: 40vh;
}
</style>