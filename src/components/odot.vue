<script>
export default { 
    data() {
        return {
            
        }
    },
    methods: {
        sendBack() {
            this.$emit("goBack");
        }
    }
};

</script>

<template>
    <div id="odot">
        <div id="allInfo">
            <div class="container">
                <div class="info">
                    <b>מומחה תוכן</b>
                    <div class="smallerFont">
                        רס"ל אביב אואנונו  
                    </div>
                </div>
                <div class="info">
                    <b>פיתוח</b>
                    <div class="smallerFont">
                        טוראי שירה כהן 
                    </div>
                </div>
                <div class="info">
                    <b>עיצוב</b>
                    <div class="smallerFont">
                        סמל לוטם גרוס <br>
                        טוראי ליאור הר צבי  
                    </div>
                </div>
                <div class="info">
                    <b>רת"ח מו"פ וחדשנות בלמידה</b>
                    <div class="smallerFont">
                        רס"ל אביב אואנונו  
                    </div>
                </div>
                <div class="info">
                    <b>רמ"ד טי"ל</b>
                    <div class="smallerFont">
                        רס"ם שלומי אוגרן
                    </div>
                </div>
                <div class="info">
                    <b>גרסה</b>
                    <div class="smallerFont">
                        פברואר 2023
                    </div>
                </div>
                <div class="info">
                    <b>צור קשר:</b>
                    <div class="smallerFont">
                        מייל: mador.till@gmail.com <br>
                        טלפון שלומי אוגרן: 052-5364232<br>
                        טלפון אביב אואנונו: 052-8394566<br>
                    </div>
                </div>
            </div>
            
        </div>
        <button type="button" class="playAnimationOnButton previous" @click="sendBack">חזרה לפתיחה</button>
    </div>
</template>


<style scoped>
#odot {
    font-family: "heebo";
    display: flex;
    flex-direction: column;
    align-items: center;
}

.smallerFont {
    font-size: 4.3vw;
}

.previous {
    width: 45vw;
    height: 10vh;
    position: absolute;
    top: 80vh;
    padding-bottom: 1vh;
    border-style: none;
    background-color: transparent;
    font-size: 2.5vmax;
    background-image: url("@/assets/images/continueButton.png");
    background-size: 100% 100%;
    color: white;
    font-family: "heebo";
}

.info {
    padding: 1vw;
    display: flex;
    flex-direction: column;
    text-align: center;
    direction: rtl;
}

#allInfo {
    margin-top: 9.6vh;
    line-height: 3.3vh;
    background-image: url("@/assets/images/explanationBoard.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    width: 85vw;
    font-size: 4.5vw;
    padding-top: 7.5vw;
    padding-left: 4vw;
    padding-right: 4vw;
    height: 68.3vh;
}

@keyframes smallerButton {
  100% {
    width: 42vw;
    height: 7vh;
    position: absolute;
    top: 82vh;
  }
}

@-webkit-keyframes smallerButton {
  100% {
    width: 42vw;
    height: 7vh;
    position: absolute;
    top: 82vh;
  }
}

.playAnimationOnButton {
  animation: smallerButton 1s ease-out forwards;
  -webkit-animation: smallerButton 1s ease-out forwards;
}
</style>