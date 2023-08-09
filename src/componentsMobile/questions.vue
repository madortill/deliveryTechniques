<script>
export default {
    props: ["questionCounter"],
    data() {
        return {
            listOfQuestions: [
                {
                    question: "מה תפקידו של המדריך בכיתה?",
                    answer1: "להעביר את המסר בכיתה", 
                    answer2: "להעניק לחניך הקשבה", 
                    answer3: "להמחיש לחניך יזואלית",
                    answer4: "לוודא הבנה",
                    correctAnswers: ["להעביר את המסר בכיתה"]
                },
                {
                    question: "על מה עלינו להקפיד בהעברת השיעור?",
                    answer1: "שימוש בטכניקות מסירה", 
                    answer2: "לתת שאלוות כל מספר דקות", 
                    answer3: "להקים את החניך מהכיסא",
                    answer4: "ליצור דיון בכיתה",
                    correctAnswers: ["שימוש בטכניקות מסירה"]
                },
                {
                    question: "מה מבין התשובת מוגדרות כטכניקות מסירה?",
                    answer1: "חיוך", 
                    answer2: "תנועות ידיים", 
                    answer3: "מצגת",
                    answer4: "שימוש בסיפור אישי",
                    correctAnswers: ["תנועות ידיים"]
                },
                {
                    question: "איזה טכניקת מסירה נפגעת בעת העברת השיעור של הרב, על פי התמונה?",
                    answer1: "תנועת גוף", 
                    answer2: "הופעה", 
                    answer3: "תנועת ידיים",
                    answer4: "קול דיבור",
                    correctAnswers: ["תנועת גוף"]
                },
                {
                    question: "כמה טכניקות מסירה קיימות?",
                    answer1: "12", 
                    answer2: "4", 
                    answer3: "8",
                    answer4: "2",
                    correctAnswers: ["8"]
                }, 
                {
                    question: "באיזה סביבה הדרכתית עלולה להיפגע טכניקת המסירה קשר עין? בחרו 2 תשובות נכונות:",
                    answer1: "כיתת מחשבים", 
                    answer2: "סדנת רכב", 
                    answer3: "כיתת לימוד",
                    answer4: "שיעור בשטח",
                    answer5: "הרצאה על במה",
                    answer6: "שיעור נהיגה מעשי ברכב",
                    correctAnswers: ["כיתת מחשבים", "שיעור נהיגה מעשי ברכב"]
                    
                },
                {
                    question: "הנך מדריך המשתמש בקול דיבור מונוטוני, מה עלול לקרות לחניכי הכיתה, בחרו 2 תשובות נכונות",
                    answer1: "החניכים לא יגלו עניין", 
                    answer2: "ניסוח לא היה תקין", 
                    answer3: "רמת הקשב תרד",
                    answer4: "ימשוך את תשומת הלב התלמידים",
                    answer5: "לא עלול לקרות כלום",
                    answer6: "ישדר חוסר בקיאות",
                    correctAnswers: ["החניכים לא יגלו עניין", "רמת הקשב תרד"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: יצירת עניין ודרמטיות",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה", 
                    answer6: "תנועות ידיים",
                    correctAnswers: ["קול דיבור"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: צמצום המרחק הפיזי",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה",
                    answer6: "תנועות ידיים",
                    correctAnswers: ["תנועות גוף"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: שמירה על דוגמא אישית",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה",
                    answer6: "תנועות ידיים",
                    correctAnswers: ["הופעה"]

                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: בקרה על מצב הלומדים",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה",
                    answer6: "תנועות ידיים",
                    correctAnswers: ["קשר עין"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: לא ללמד טעויות",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה", 
                    answer6: "תנועות ידיים",
                    correctAnswers: ["בקיאות"]
                }
            ],
            changingCharacter: [true, true, false, true, false, false, true, false, true, false, true, false],
            chosenOptions: "",
            multipleChosenOptions: [], 
            correctAnswersArray: "",
            ableToPress: false, 
            ableToCheck: true,
            answerChecked: "",
            correctAnswersChecked: 0, 
            help: "hide"
        }
    },
    methods: {
        updateQuestion() {
            this.multipleChosenOptions = [];

            this.chosenOptions = "";

            this.ableToCheck = false;
            this.ableToPress = false;

            this.$emit("level", this.changingCharacter[Number(this.questionCounter)]);
        }, 
        checkAnswer() {
            this.correctAnswersChecked = 0;
            this.correctAnswersArray = this.listOfQuestions[Number(this.questionCounter)]["correctAnswers"]; 

            if (this.correctAnswersArray.length === 2) {
                for (let i = 0; i < this.multipleChosenOptions.length; i++) {
                    for (let j = 0; j < this.correctAnswersArray.length; j++) {
                        
                        this.ableToPress = true;

                        if (this.correctAnswersArray[j] !== this.multipleChosenOptions[i].innerText) {
                            this.answerChecked = "incorrect";
                        } else {
                            this.correctAnswersChecked++; 
                            this.answerChecked = "correct";
                            break;
                        }
                    }

                    this.multipleChosenOptions[i].classList.remove("picked");
                    this.multipleChosenOptions[i].classList.add(this.answerChecked);
                }

                let AnotherTimer = setTimeout(() => {
                    for (let i = this.multipleChosenOptions.length - 1; i >= 0; i--) {
                        this.ableToCheck = false;
                        this.ableToPress = false;

                        this.multipleChosenOptions[i].disabled = true;

                        if (this.multipleChosenOptions[i].classList.contains("incorrect")) {

                            this.multipleChosenOptions[i].classList.remove("incorrect");
                            this.multipleChosenOptions[i].classList.add("disabled");

                            this.multipleChosenOptions.splice(i,1);
                            this.ableToCheck = true;
                        }
                    }
                }, 1000); 

                if (this.correctAnswersChecked === 2) {
                    this.ableToCheck = true;
                    this.ableToPress = true;
                    let timer = setTimeout(this.updateQuestion, 1200);
                }

            } else {
                if (this.chosenOptions !== undefined) {
                    this.chosenOptions.classList.remove("picked");
                }
                this.ableToCheck = true;
                this.ableToPress = true;

                if (this.chosenOptions.innerText === this.correctAnswersArray[0]) {

                    this.chosenOptions.classList.add("correct");
                    let timer = setTimeout(this.updateQuestion, 1200);
                } else {
                    this.chosenOptions.classList.add("incorrect");

                    let AnotherTimer = setTimeout(() => {
                        this.chosenOptions.classList.remove("incorrect");
                        this.chosenOptions.classList.add("disabled");

                        this.ableToPress = false;
                        this.chosenOptions.style.pointerEvents = "none";
                    }, 1000);
                }
            }

        },
        pickAnswers(event) {   
            if (this.listOfQuestions[this.questionCounter]["correctAnswers"].length === 2) {

                if (event.currentTarget.classList.contains("picked")) {
                    event.currentTarget.classList.remove("picked");
                    let index = this.multipleChosenOptions.indexOf(event.currentTarget);
                    this.multipleChosenOptions.splice(index, 1);
                } else {
                    if (this.multipleChosenOptions.length < 2) {
                        event.currentTarget.classList.add("picked");
                        this.multipleChosenOptions.push(event.currentTarget);
                    }
                }

                if (this.multipleChosenOptions.length > 0) {
                    this.ableToCheck = false;
                }
            } else {
                if (this.chosenOptions !== "") {
                    this.chosenOptions.classList.remove("picked");
                }
                this.ableToCheck = false;
                this.chosenOptions = event.currentTarget;
                event.currentTarget.classList.toggle("picked");
            }
        },
        showPicture() {
            if (this.help === "hide") {
                this.help = "show";
            } else {
                this.help = "hide";
            }
        }
    }  
};
</script>



<template>
    <div id="questions">
        <div class="questionContainer">
            <div class="level"><b>טכניקות מסירה</b></div>
            <div id="question">{{ listOfQuestions[Number(questionCounter)]["question"] }}</div>
            <div id="help" v-show="this.questionCounter === 3" @click="showPicture">לצפייה בתמונה</div>
            <img src="https://lh4.googleusercontent.com/Ezh_FXiYmVyAkwJ6SFS815F5caWhBdqXJT9MfIs1nIdpXcdokTCnRe2ymqn103botttD5Yu0ri4Sf8Wt1cHPZMQWf_TLnawpuGUj-khdZCbQxHuFxc2AO0uy_IcCvewUpg=w740" alt="Captionless Image" id="picture" :class="help === 'hide' ? 'hidden' : 'show'" />
        </div>
        <div v-for="answer in listOfQuestions" :key="answer.question" v-show="listOfQuestions[Number(questionCounter)]['question'] === answer.question" class="containerForAnswers">
            <button v-for="(content, key) in answer" :key="key" v-show="key.includes('answer')" class="answers" @click="pickAnswers" :disabled="ableToPress">{{ content }}</button>
        </div>
        <button type="button" id="check" @click="checkAnswer" :disabled="ableToCheck">בדוק אותי</button>
    </div>
</template>


<style scoped>

.hidden {
    visibility: hidden;
} 

.show {
    visibility: visible;
}

#help {
  width: 37vw;
  height: 6vh;
  background-image: url("@/assets/images/continueButton.png");
  background-size: 100% 100% ;
  color: white;
  margin-right: 40vw;
}

#questions {
    padding: 2vh;
    display: flex;
    flex-direction: column;
    margin-top: 1vh;
    direction: rtl;
    text-align: center;
    align-items: center;
    justify-content: flex-start;
    height: 100vh;
}

.level {
    margin-top: 3vh;
    text-align: center;
    direction: rtl;
    font-size: 4vh;
}

#check {
    width: 42vw;
    height: 7vh;
    border-style: none;
    background-color: transparent;
    font-size: 2.5vmax;
    padding-bottom: 1vh;
    background-image: url("@/assets/images/continueButton.png");
    background-size: 100% 100%;
    font-family: "heebo";
    color: white;
    position: absolute;
    top: 82vh;
}

.questionContainer {
    margin-top: 8vh;
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    width: 100vw;
    height: 37vh;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#question {
    text-align: center;
    margin-top: 3vh;
    font-size: 6vw;
    direction: rtl;
    width: 87vw;
}

.answers {
    background-image: url("@/assets/images/answerButton.png");
    background-size: 100% 100%;
    background-color: transparent;
    border-style: none;
    font-family: "heebo";
    color: white;
    margin-top: 1vh;
    width: 33vw;
    height: 10.5vh;
    font-size: 4.4vw;
}

#picture {
    width: 74vw;
    z-index: 100;
    margin-top: 2vh;
}

.containerForAnswers {
    width: 100vw;
    height: 25vh;
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.disabled {
    background-image: url("@/assets/images/beenThere.svg");
}

.correct {
    background-image: url("@/assets/images/correct.png");
}

.incorrect {
    background-image: url("@/assets/images/incorrectButton.svg");
}

.picked {
    background-image: url("@/assets/images/currently.svg");
}

button:disabled,
button[disabled] {
    border-color: black;
    color: white;
}
</style>