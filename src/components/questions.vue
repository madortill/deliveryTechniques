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
                    src: "",
                    answer1: "תנועת גוף", 
                    answer2: "הופעה", 
                    answer3: "תנועת ידיים",
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
                    correctAnswers: ["החניכים לא יגלו עניין", "רמת הקשב תרד"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: יצירת עניין ודרמטיות",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה", 
                    correctAnswers: ["קול דיבור"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: צמצום המרחק הפיזי",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה",
                    correctAnswers: ["תנועות גוף"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: שמירה על דוגמא אישית",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה",
                    correctAnswers: ["הופעה"]

                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: בקרה על מצב הלומדים",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה",
                    correctAnswers: ["קשר עין"]
                },
                {
                    question: "התאם בין טכניקת המסירה אל בין מטרתה העיקרית: לא ללמד טעויות",
                    answer1: "קול דיבור", 
                    answer2: "תנועות גוף", 
                    answer3: "בקיאות",
                    answer4: "קשר עין",
                    answer5: "הופעה", 
                    correctAnswers: ["בקיאות"]
                }
            ],
            chosenOptions: "",
            multipleChosenOptions: [], 
            correctAnswersArray: "",
            ableToPress: false, 
            ableToCheck: true,
            answerChecked: "",
            correctAnswersChecked: 0

        }
    },
    methods: {
        updateQuestion() {
            this.ableToCheck = true;
            this.ableToPress = false; 

            this.multipleChosenOptions = [];

            this.chosenOptions = "";
            this.$emit("level");
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
                        
                        this.multipleChosenOptions[i].disabled = true;

                        if (this.multipleChosenOptions[i].classList.contains("incorrect")) {

                            this.multipleChosenOptions[i].classList.remove("incorrect");
                            this.multipleChosenOptions[i].classList.add("disabled");

                            this.ableToPress = false;                            
                            this.multipleChosenOptions.splice(i,1);
                        }
                    }
                }, 1000); 

                console.log(this.correctAnswersChecked);
                if (this.correctAnswersChecked === 2) {
                    this.ableToCheck = true;
                    this.ableToPress = true;
                    let timer = setTimeout(this.updateQuestion, 1200);
                }

            } else {
                this.chosenOptions.classList.remove("picked");

                if (this.chosenOptions.innerText === this.correctAnswersArray[0]) {
                    this.ableToCheck = true;
                    this.ableToPress = true;

                    this.chosenOptions.classList.add("correct");
                    let timer = setTimeout(this.updateQuestion, 1200);
                } else {
                    this.ableToPress = true;
                    this.chosenOptions.classList.add("incorrect");

                    let AnotherTimer = setTimeout(() => {
                        this.chosenOptions.classList.remove("incorrect");
                        this.chosenOptions.classList.add("disabled");
                        this.ableToPress = false;
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
        }
    }  
};
</script>



<template>
    <div id="questions">
        <div class="questionContainer">
            <div class="level"><b>טכניקות מסירה</b></div>
            <div id="question">{{ listOfQuestions[Number(questionCounter)]["question"] }}</div>
        </div>
        <div v-for="answer in listOfQuestions" :key="answer.question" v-if="listOfQuestions[Number(questionCounter)]['question'] === answer.question" class="containerForAnswers">
            <button v-for="(content, key) in answer" :key="key" v-show="key.includes('answer')" class="answers" @click="pickAnswers" :disabled="ableToPress">{{ content }}</button>
        </div>
        <button type="button" id="check" @click="checkAnswer" :disabled="ableToCheck">בדוק אותי</button>
    </div>
</template>


<style scoped>
#questions {
    padding: 2vh;
    display: flex;
    flex-direction: column;
    margin-top: 1vh;
    direction: rtl;
    text-align: center;
    /* color: black; */
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
    font-size: 5.5vw;
    padding-bottom: 1vh;
    background-image: url("@/assets/images/continueButton.png");
    background-size: 100% 100%;
    font-family: "heebo";
    color: white;
    position: relative;
    top: 22vh;
}

.questionContainer {
    margin-top: 10vh;
    background-image: url("@/assets/images/board.png");
    background-size: 100% 100%;
    width: 100vw;
    height: 30vh;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#question {
    text-align: center;
    margin-top: 3vh;
    font-size: 6vw;
    direction: rtl;
    width: 90vw;
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
    height: 8.3vh;
    font-size: 4.45vw;
}

.containerForAnswers {
    width: 100vw;
    height: 20vh;
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
    background-image: url("@/assets/images/correctButton.svg");
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