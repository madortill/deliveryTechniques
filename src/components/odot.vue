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
        <button type="button" class="playAnimationOnButton previous" @click="sendBack">חזרה לפתיחה</button>
    </div>
</template>


<style scoped>
#odot {
    font-family: "heebo";
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
}

.smallerFont {
    font-size: 0.7vmax;
}

.previous {
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

.info {
    padding: 0.2vw;
    text-align: center;
    direction: rtl;
}

#allInfo {
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    transform: scale(1.75, 1.75);
    background-repeat: no-repeat;
    height: 22.5vh;
    width: 25vw;
    margin-top: 3vh;
    display: flex;
    flex-wrap: wrap;
    direction: rtl;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 0.9vmax;
    padding-top: 2.5vh;
    padding-left: 2.5vw;
    padding-bottom: 5vh;
    padding-right: 2.5vw;
}

/* @keyframes smallerButton {
  100% {
    width: 42vw;
    height: 7vh;
  }
}

@-webkit-keyframes smallerButton {
  100% {
    width: 42vw;
    height: 7vh;
  }
} */

 /* .playAnimationOnButton {
  animation: smallerButton 1s ease-out forwards;
  -webkit-animation: smallerButton 1s ease-out forwards;
} */ 
</style>