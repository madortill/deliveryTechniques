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
                    sayingBubble: "היום נעבור שיעור על טכניקות מסירה!"
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
            // debugger;
            this.dontPressCharacter = true;
            this.isGlow = false;
            
            let timer = setTimeout (() => {
                // debugger;
                this.isGlow = true;
                this.$emit("update");
            }, 1000);
        }
    }
};
</script>


<template>
    <div id="character">
        <div ref="soldier" class="soldierGlow" @click="updateQuestion" :disabled="dontPressCharacter" :class="isGlow ? [currentCharacter, 'soldierGlow'] : [toggleGlow, 'soldier']" :id="isGlow ? `level${questionCounter}Glow` : `level${questionCounter}`"></div>
        <div class="bubble">{{ characterImages[questionCounter]["sayingBubble"] }}</div>
    </div>
</template>


<style scoped>
body::after {
    content: url("/soldier1Glow.svg"), url("/soldier2Glow.svg"), url("/soldier3Glow.svg"), url("/soldier4Glow.svg"), url("/soldier5Glow.svg"), url("/soldier1.svg"), url("/soldier2.svg"), url("/soldier3.svg"), url("/soldier4.svg"), url("/soldier5.svg");
}
.bubble {
    position: absolute;
    top: 19vh;
    left: 27vw;
    width: 40vw;
    font-size: 4.5vw;
    text-align: center;
    direction: rtl;
}
.level0Glow {
    background-image: url("/soldier1Glow.svg");
}

.level1Glow {
    background-image: url("/soldier1Glow.svg");
}

.level2Glow {
    background-image: url("/soldier1Glow.svg");
}

.level3Glow {
    background-image: url("/soldier2Glow.svg");
}

.level4Glow {
    background-image: url("/soldier2Glow.svg");
}

.level5Glow {
    background-image: url("/soldier2Glow.svg");
}

.level6Glow {
    background-image: url("/soldier3Glow.svg");
}

.level7Glow {
    background-image: url("/soldier3Glow.svg");
}

.level8Glow {
    background-image: url("/soldier4Glow.svg");
}

.level9Glow {
    background-image: url("/soldier4Glow.svg");
}

.level10Glow {
    background-image: url("/soldier5Glow.svg");
}

.level11Glow {
    background-image: url("/soldier5Glow.svg");
}

.level0 {
    background-image: url("/soldier1.svg");
}

.level1 {
    background-image: url("/soldier1.svg");
}

.level2 {
    background-image: url("/soldier1.svg");
}

.level3 {
    background-image: url("/soldier2.svg");
}

.level4 {
    background-image: url("/soldier2.svg");
}

.level5 {
    background-image: url("/soldier2.svg");
}

.level6 {
    background-image: url("/soldier3.svg");
}

.level7 {
    background-image: url("/soldier3.svg");
}

.level8 {
    background-image: url("/soldier4.svg");
}

#level8Glow {
    position: relative;
    bottom: 7vh;
    left: 12vw;
}

#level8 {
    transform: scale(2);
}

#level10Glow {
    position: relative;
    left: 8vw;
}

#level10 {
    transform: scale(2);
}

#level3 {
    position: relative;
    left: 3vw;
    top: 29vh;
}

#level3Glow {
    position: relative;
    left: -4vw;
}

#level6 {
    position: relative;
    top: 28vh;
    left: 3vw;
}

#level6Glow {
    position: relative;
    top: 2vh;
}


.level9 {
    background-image: url("/soldier4.svg");
}

.level10 {
    background-image: url("/soldier5.svg");
}

.level11 {
    background-image: url("/soldier5.svg");
}

#character {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    align-content: center;
    align-items: center;
}

.soldierGlow {
    background-size: 120% 117%;
    transform: scale(1.5);
    background-repeat: no-repeat;
    width: 100vw;
    height: 600vh;
}

.soldier {
    background-size: 100% 100%;
    transform: scale(1.5);
    background-repeat: no-repeat;
    position: relative;
    top: 27vh;
    width: 53vw;
    height: 77vh;
}
</style>