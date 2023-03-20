<script>
    import instructionsVue from './instructions.vue';        
    export default {
        data() {
            return {
                pressed: false,
                chosenButton: "",
                help: "hide",
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
                        extra2: `לכן נאמר כי טכניקת הבקיאות היא "אם כל הטכניקות"`
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
                if (this.help === "hide") {
                    this.help = "show";
                } else {
                    this.help = "hide";
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
            <div id="instruction" ref="instruction" :class="help === 'hide' ? 'hidden' : 'show'">בלחיצה על טכניקת המסירה יופיע ההסבר המתאים</div>
            <div id="videoSummary">
                <div class="buttonContainer">
                    <button type="button" class="buttons answers" v-for="info in texts" :key="info.buttonName + ' btn'" @click="recognizeButton">{{ info.buttonName }}</button>
                </div>
                <div class="board playAnimation">
                    <div v-for="info in texts" :key="info.buttonName + ' text'" v-show="chosenButton === info.buttonName" id="text">
                        <div v-show="info.extra1">
                            {{ info.extra1 }}
                        </div>
                        <ul>
                            <li v-for="(content, key) in info" :key="key" v-show="key.includes('line')">
                                {{ content }}
                            </li>
                        </ul>
                        <div v-show="info.extra2">{{ info.extra2 }}</div>
                    </div>
                </div>
            </div>
            <button type="button" id="nextPage" @click="nextPage">נמשיך לתרגול</button>
            <button type="button" id="prevPage" @click="prevPage">חזרה לסרטון</button>
        </div>
        <instructionsVue v-else @prevPage="showPage"></instructionsVue>
    </div>
</template> 

<style scoped>
@font-face {
  font-family: "heebo";
  src: url("C:/Users/USER/Documents/projects/לומדת טכניקת מסירה/src/assets/Heebo/Heebo-VariableFont_wght.ttf");
}

#videoSummary {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    position: relative;
    bottom: 3.5vh;
}

#explanationPage {
  font-family: "heebo";
  user-select: none;
  overflow: hidden;
}

#instruction {
    direction: rtl;
    text-align: center;
    position: relative;
    z-index: 100;
    background-color: rgba(255, 255, 255, 0.856);
    border-radius: 3vw;
    padding-top: 1vh;
    padding-bottom: 1vh;
    top: 2vh;
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
    height: 22vh;
    display: flex;
    flex-wrap: wrap;
    width: 100vw;
    flex-direction: column;
    justify-content: space-evenly;
}

#help {
  width: 7vw;
  height: 4vh;
  position: relative;
  left: 45vw;
  top: 1vh;
}
.summary {
    display: flex; 
    width: 100vw;
    height: 100vh;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-items: center;
    align-content: center;
}

#nextPage {
    font-size: 5.5vw;
    padding-bottom: 1vh;
    width: 42vw;
    height: 7vh;
    font-family: "heebo";
    position: fixed;
    bottom: 8vh;
    left: 4vw;
    background-image: url("@/assets/images/continueButton.png");
    background-size: 100% 100%;
    background-color: transparent;
    border-style: none;
    color: white;
}

#prevPage {
    font-size: 5.5vw;
    padding-bottom: 1vh;
    width: 42vw;
    height: 7vh;
    font-family: "heebo";
    position: fixed;
    bottom: 8vh;
    right: 4vw;
    background-image: url("@/assets/images/continueButton.png");
    background-size: 100% 100%;
    background-color: transparent;
    border-style: none;
    color: white;
}

.board {
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    width: 108vw;
    height: 52.3vh;
    position: relative;
    bottom: 30vh;
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
    width: 32vw;
    height: 7vh;
    margin-left: 1vw;
    background-size: 100% 100%;
    font-size: 4.5vw;
    background-color: transparent;
    border-style: none;
    color: white;
    font-family: "heebo";
}

#text {
    padding-top: 4.1vh;
    padding-left: 4.4vh;
    font-size: 4.75vw;
    direction: rtl;
    width: 85vw;
}

</style>