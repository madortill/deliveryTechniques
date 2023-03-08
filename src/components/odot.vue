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
        <button type="button" id="previous" @click="sendBack">חזרה לפתיחה</button>
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
    font-size: 4.5vw;
}

#previous {
    width: 42vw;
    height: 7vh;
    padding-bottom: 1vh;
    border-style: none;
    background-color: transparent;
    font-size: 5.5vw;
    margin-bottom: 6vh;
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
    margin-top: 10vh;
    line-height: 3.4vh;
    background-image: url("src/assets/images/explanationBoard.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    width: 85vw;
    padding-top: 8vw;
    padding-left: 5vw;
    padding-right: 5vw;
    height: 70.5vh;
}
</style>