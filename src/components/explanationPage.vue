<script>
    import instructionsVue from './instructions.vue';        
    export default {
        data() {
            return {
                pressed: false,
                chosenButton: "",
                help: "none",
                pressedButton: [], 
                texts: [
                    {
                        buttonName: "כניסה לכיתה",
                        line1: "כניסת המדריך צריכה להיות בזמן",
                        line2: "על החניכים להיכנס בצורה רגועה",
                        line3: `על המדריך להיות בשקט בעת כניסת המדריך ולקבלו ב"הקשב"`,
                        line4: "על המדריך להתייחס אל חניכיו ולשלומם לפני העברת החומר הלימודי",
                        line5: "על המדריך להיות בקיא במצבת החניכים ובהיעדרוית הצפויות במהלך השיעור"
                    },
                    {
                        buttonName: "הופעת המדריך",
                        line1: "הרושם הראשוני שיוצר המדריך - יש לו השפעה רבה על כל תהליך הלמידה",
                        line2: "הימנעות ממסרים סותרים",
                        line3: "המדריך משמש דוגמא אישית לחניכיו בכל העת, ועליו להקפיד על הופעה תקנית ונאותה (פרט למקרים בהם לא ניתן לעשות זאת מסיבות בטחוניות)",
                        line4: "על המדריך להקפיד על הופעתם התקנית של חניכיו לאורך השיעור"

                    },
                    {
                        buttonName: "קשר עין",
                        line1: "להקפיד על חלוקת מבטים שווה בכיתה, ללא התמקדות בחניך או בחפץ מסוים (קירות, תקרה, לוח וכו')",
                        line2: "בעת מענה על שאלת חניך רוב הזמן נקדיש לו את קשר שלנו, אך נדאג לפזר מבטים גם לשאר החניכים (80/20)",
                        line3: "נסתכל בעיניי החניך"
                    },
                    {
                        buttonName: "קול דיבור",
                        line1: `שימוש בקול בדיבור נקפיד על עוצמה, לא מונוטניוות, וקצב הולם את הנושא (עמ"ק)`
                    },
                    {
                        buttonName: "ניסוח",
                        line1: "נקפיד לנסח בעברית תקינה",
                        line2: "נתאים את הניסוח לרמת החניכים",
                        line3: `נקפיד להסביר מונחים מקצועיים ור"ת`,
                        line4: `נשמור על "שם המספר"`,
                        line5: "נצמצם שימוש במילים לועזיות",
                        line6: "נמנע מסלנג או שפה נמוכה"
                    },
                    {
                        buttonName: "תנועת גוף",
                        line1: "על תנועת הגוף להיות טבעית, להביע עוצמה וסמכותיות",
                        line2: "עלינו לנצל את כל המרחב ההדרכתי הניתן לרשותנו",
                        line3: "עלינו להימנע ממונוטניות בתנועות הגוף",
                        line4: "עלינו להתאים בין קצב תנועות הגוף לקצב הדיבור",
                        line5: "נרים רגליים",
                        line6: "עלינו להימנע מלעמדו זמן ממושך בפני המקרן",
                    },
                    {
                        buttonName: "תנועות ידיים",
                        line1: "נקפיד תנועות הידיים חופשיות ממחישות את המסר",
                        line2: "תנוועות הידיים יתאימו לקצב הדיבור",
                        line3: "עלינו להימנע מלהחזיק חפצים ביד, כמו כן להכניס ידיים לכיסים, חגורה וכו'"
                    },
                    {
                        buttonName: "בקיאות",
                        extra1: "אי בקיאות המדריך בחומר עלולה להוביל ל-",
                        line1: "איבוד אמון החניכים",
                        line2: "חוסר תשומת לב החניכים",
                        line3: "קשיים בהעברת החומר בצורה מעניינת - מגיעה בשאר טכניקות המסירה",
                        line4: "לימוד טעויות!",
                        extra2: `לכן נאמר כי טכניקת הבקיאות היא "אם כל הטכניקות".`
                    },
                ]
            }
        }, 
        methods: {
            nextPage() {
                this.pressed = true;
            },
            recognizeButton(event) {
                this.chosenButton = event.currentTarget.innerText;
                event.currentTarget.classList.remove("answers");

                if (!this.pressedButton.includes(event.currentTarget)) {
                    this.pressedButton.push(event.currentTarget);
                }

                for (let i = 0; i < this.pressedButton.length; i++) {
                    this.pressedButton[i].classList.remove("current");
                    this.pressedButton[i].classList.add("beenThere");
                }
                event.currentTarget.classList.remove("beenThere");
                event.currentTarget.classList.add("current");
            }, 
            showInstruction() {
                if (this.help === "none") {
                    this.help = "block";
                } else {
                    this.help = "none";
                }
            }, 
            prevPage() {
                this.$emit('backPage');
            }, 
            showPage() {
                this.pressed = false;
            }
        }, 
        components: { instructionsVue }
    };
</script>

<template>
    <div id="explanationPage">
        <div class="summary" v-if="pressed === false">
            <img src="@/assets/images/help.png" alt="help" id="help" @click="showInstruction"/>
            <div id="instruction" ref="instruction" :class="help === 'none' ? 'none' : 'block'">בלחיצה על טכניקת המסירה יופיע ההסבר המתאים</div>
            <!-- <div id="videoSummary"> -->
                <div class="buttonContainer">
                    <button type="button" class="buttons answers" v-for="info in texts" :key="info.buttonName + ' btn'" @click="recognizeButton">{{ info.buttonName }}</button>
                </div>
                <div class="board playAnimation">
                    <div v-for="info in texts" :key="info.buttonName + ' text'" v-show="chosenButton === info.buttonName" id="text">
                        <div v-show="info.extra1" class="text2" :class="info.extra1 !== '' ? 'block' : 'none'">
                            {{ info.extra1 }}
                        </div>
                        <ul>
                            <li v-for="(content, key) in info" :key="key" v-show="key.includes('line')">
                                {{ content }}
                            </li>
                        </ul>
                        <div v-show="info.extra2" class="text2" :class="info.extra2 !== '' ? 'block' : 'none' ">{{ info.extra2 }}</div>
                    </div>
                </div>
            <!-- </div> -->
            <div class="flex">
                <button type="button" id="nextPage" @click="nextPage">נמשיך לתרגול</button>
                <button type="button" id="prevPage" @click="prevPage">חזרה לסרטון</button>
            </div>
        </div>
        <instructionsVue v-else @prevPage="showPage"></instructionsVue>
    </div>
</template> 

<style scoped>
@font-face {
  font-family: "heebo";
  src: url("C:/Users/USER/Documents/projects/לומדת טכניקת מסירה/src/assets/Heebo/Heebo-VariableFont_wght.ttf");
}

.flex {
    display: flex;
    justify-content: space-evenly;
    width: 100%;
}

.text2 {
    padding-right: 2vw;
    line-height: 1.5vh;
}

#videoSummary {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
}

#explanationPage {
    height: 100%;
    width: 100%;
    font-family: "heebo";
    user-select: none;
    overflow: hidden;
}

#instruction {
    direction: rtl;
    text-align: center;
    position: absolute;
    z-index: 100;
    background-color: rgba(255, 255, 255, 0.9);
    border-radius: 1vw;
    padding: 3vh 1vh;
    top: 5vh;
}

.none {
    display: none;
}

.block {
    position: fixed;
    display: block;
}

.hidden {
    visibility: hidden;
} 

.show {
    visibility: visible;
}

.current {
    background-image: url("@/assets/images/currently.svg");
}

.beenThere {
    background-image: url("@/assets/images/beenThere.svg");
}

.answers {
    background-image: url("@/assets/images/answerButton.png");
}
.buttonContainer {
    height: 20vh;
    display: flex;
    flex-wrap: wrap;
    width: 60vw;
    flex-direction: row-reverse;
    justify-content: center;
}

#help {
    width: 2.2vw;
    height: 3.75vh;
    position: absolute;
    right: 1vw;
    top: 1vh;
}
.summary {
    display: flex;
    /* width: 100vw; */
    height: 100%;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: space-around;
    align-items: center;
}

#nextPage {
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

#prevPage {
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

.board {
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    transform: scale(1.75, 1.75);
    background-repeat: no-repeat;
    height: 30vh;
    width: 30vw;
    position: relative;
    bottom: 23vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.playAnimation {
  animation: lowerBoard 1s ease-out forwards;
  -webkit-animation: lowerBoard 1s ease-out forwards;
}

@keyframes lowerBoard {
  100% {
    bottom: 0vh;
  }
}

@-webkit-keyframes lowerBoard {
  100% {
    bottom: 0vh;
  }
}

.buttons {
    width: 12vw;
    height: 6.5vh;
    margin-left: 1vw;
    background-size: 100% 100%;
    font-size: 1.5vmax;
    background-color: transparent;
    border-style: none;
    color: white;
    font-family: "heebo";
}

#text {
    /* padding-top: 4.1vh; */
    /* padding-right: 1.7vh; */
    font-size: 1.5vh;
    height: 80%;
    /* font-size: 4.7vw; */
    direction: rtl;
    width: 87%;
}

</style>