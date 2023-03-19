<script>
export default {
    props: ["questionCounter"],
    data() {
        return {
            isGlow: true,
            characterImages: [
                {
                    sayingBubble: ""
                },
                {
                    sayingBubble: "*לוחשת*"
                },
                {
                    sayingBubble: ""
                }, 
                {
                    sayingBubble: "אממ"
                },
                {
                    sayingBubble: ""
                }, 
                {
                    sayingBubble: ""
                },
                {
                    sayingBubble: "אממ"
                }, 
                {
                    sayingBubble: ""
                },
                {
                    sayingBubble: "היום נעבור שיעור על טכניקות מסירה"
                }, 
                {
                    sayingBubble: ""
                }, 
                {
                    sayingBubble: ""
                },
                {
                    sayingBubble: "*בבטחון* נעבור הנושאים הבאים"
                }
            ],
            dontPressCharacter: false
        }
    }, 
    computed: {
        currentCharacter(isGlow) {
            // if (isGlow) {
                return (`level${this.questionCounter}Glow`); 
            // } 
            // else {
            //     return (`level${this.questionCounter}`); 
            // }
        },
        toggleGlow() {
            return (`level${this.questionCounter}`); 
        }
    }, 
    methods: {
        updateQuestion() {
            this.dontPressCharacter = true;

            // let newPicture = this.characterImages[this.questionCounter][`level${this.questionCounter}`].slice(1, -8);
            // console.log(newPicture);
            // console.log(this.$refs.soldier);
            // this.$refs.soldier.backgroundImage = `url("/public/${newPicture}.png")`;
            // console.log(this.$refs.soldier.backgroundImage);
            // this.characterImages[this.questionCounter][`level${this.questionCounter}`] = `${newPicture}.png`;

            this.isGlow = false;
            
            let timer = setTimeout (() => {
                this.$emit("update");
            }, 1000);
        }
    }
};

</script>


<template>
    <div id="character">
        <div id="soldier" @click="updateQuestion" :disabled="dontPressCharacter" :class="isGlow ? currentCharacter : toggleGlow"></div>
        <!-- <img :src="currentCharacter" alt="soldier" id="soldier" @click="updateQuestion" :disabled="dontPressCharacter"/> -->
    </div>
</template>



<style scoped>
.level0Glow {
    background-image: url("/soldier1Glow.png");
}

.level1Glow {
    background-image: url("/soldier1Glow.png");
}

.level2Glow {
    background-image: url("/soldier1Glow.png");
}

.level3Glow {
    background-image: url("/soldier2Glow.png");
}

.level4Glow {
    background-image: url("/soldier2Glow.png");
}

.level5Glow {
    background-image: url("/soldier2Glow.png");
}

.level6Glow {
    background-image: url("/soldier3Glow.png");
}

.level7Glow {
    background-image: url("/soldier3Glow.png");
}

.level8Glow {
    background-image: url("/soldier4Glow.png");
}

.level9Glow {
    background-image: url("/soldier4Glow.png");
}

.level10Glow {
    background-image: url("/soldier5Glow.png");
}

.level11Glow {
    background-image: url("/soldier5Glow.png");
}

.level0 {
    background-image: url("/soldier1.png");
}

.level1 {
    background-image: url("/soldier1.png");
}

.level2 {
    background-image: url("/soldier1.png");
}

.level3 {
    background-image: url("/soldier2.png");
}

.level4 {
    background-image: url("/soldier2.png");
}

.level5 {
    background-image: url("/soldier2.png");
}

.level6 {
    background-image: url("/soldier3.png");
}

.level7 {
    background-image: url("/soldier3.png");
}

.level8 {
    background-image: url("/soldier4.png");
}

.level9 {
    background-image: url("/soldier4.png");
}

.level10 {
    background-image: url("/soldier5.png");
}

.level11 {
    background-image: url("/soldier5.png");
}

#character {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    align-content: center;
    align-items: center;
}

#soldier {
    background-size: 100% 100%;
    width: 57vw;
    position: relative;
    top: 15vh;
    height: 75vh;
}
</style>