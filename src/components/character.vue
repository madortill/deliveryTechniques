<script>
export default {
    props: ["questionCounter"],
    data() {
        return {
            isGlow: true,
            characterImages: [
                {
                    sayingBubble: "..."
                },
                {
                    sayingBubble: "מה לומר להם?"
                },
                {
                    sayingBubble: ""
                }, 
                {
                    sayingBubble: "..."
                },
                {
                    sayingBubble: ""
                }, 
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
                    sayingBubble: "!היום נעבור שיעור על טכניקות מסירה"
                }, 
                {
                    sayingBubble: ""
                }, 
                {
                    sayingBubble: "נעבור על הנושאים הבאים"
                },
                {
                    sayingBubble: ""
                }
            ],
            dontPressCharacter: false
        }
    }, 
    computed: {
        currentCharacter() {
            return (`level${this.questionCounter}Glow`); 
        },
        toggleGlow() {
            return (`level${this.questionCounter}`); 
        }
    }, 
    methods: {
        updateQuestion() {
            this.dontPressCharacter = true;
            this.isGlow = false;
            
            let timer = setTimeout (() => {
                this.isGlow = true;
                this.$emit("update");
            }, 1000);
        }
    }
};
</script>


<template>
    <div id="character">
        <div id="soldier" @click="updateQuestion" :disabled="dontPressCharacter" :class="isGlow ? currentCharacter : toggleGlow"></div>
        <div class="bubble">{{ characterImages[questionCounter]["sayingBubble"] }}</div>
    </div>
</template>


<style scoped>
.bubble {
    position: absolute;
    top: 18vh;
    left: 18vw;
    width: 40vw;
    font-size: 4.5vw;
    text-align: center;
    direction: rtl;
}
.level0Glow {
    background-image: url("/soldier1Glow.png");
    width: 57vw;
}

.level1Glow {
    background-image: url("/soldier1Glow.png");
    width: 57vw;
}

.level2Glow {
    background-image: url("/soldier1Glow.png");
    width: 57vw;
}

.level3Glow {
    background-image: url("/soldier2Glow.png");
    width: 57vw;
}

.level4Glow {
    background-image: url("/soldier2Glow.png");
    width: 57vw;
}

.level5Glow {
    background-image: url("/soldier2Glow.png");
    width: 57vw;
}

.level6Glow {
    background-image: url("/soldier3Glow.png");
    width: 57vw;
}

.level7Glow {
    background-image: url("/soldier3Glow.png");
    width: 57vw;
}

.level8Glow {
    background-image: url("/soldier4Glow.png");
    width: 67vw;
}

.level9Glow {
    background-image: url("/soldier4Glow.png");
    width: 67vw;
}

.level10Glow {
    background-image: url("/soldier5Glow.png");
    width: 67vw;
}

.level11Glow {
    background-image: url("/soldier5Glow.png");
    width: 67vw;
}

.level0 {
    background-image: url("/soldier1.png");
    width: 57vw;
}

.level1 {
    background-image: url("/soldier1.png");
    width: 57vw;
}

.level2 {
    background-image: url("/soldier1.png");
    width: 57vw;
}

.level3 {
    background-image: url("/soldier2.png");
    width: 57vw;
}

.level4 {
    background-image: url("/soldier2.png");
    width: 57vw;
}

.level5 {
    background-image: url("/soldier2.png");
    width: 57vw;
}

.level6 {
    background-image: url("/soldier3.png");
    width: 57vw;
}

.level7 {
    background-image: url("/soldier3.png");
    width: 57vw;
}

.level8 {
    background-image: url("/soldier4.png");
    width: 67vw;
}

.level9 {
    background-image: url("/soldier4.png");
    width: 67vw;
}

.level10 {
    background-image: url("/soldier5.png");
    width: 67vw;
}

.level11 {
    background-image: url("/soldier5.png");
    width: 67vw;
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
    position: relative;
    top: 15vh;
    height: 75vh;
}
</style>