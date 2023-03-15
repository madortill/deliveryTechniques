<script>
export default {
    props: ["questionCounter"],
    data() {
        return {
            characterImages: [
                {
                    level0: "/soldier1Glow.png",
                    sayingBubble: ""
                },
                {
                    level1: "/soldier1Glow.png",
                    sayingBubble: "*לוחשת*"
                },
                {
                    level2: "/soldier1Glow.png",
                    sayingBubble: ""
                }, 
                {
                    level3: "/soldier2Glow.png", 
                    sayingBubble: "אממ"
                },
                {
                    level4: "/soldier2Glow.png",
                    sayingBubble: ""
                }, 
                {
                    level5: "/soldier2Glow.png",
                    sayingBubble: ""
                },
                {
                    level6: "/soldier3Glow.png",
                    sayingBubble: "אממ"
                }, 
                {
                    level7: "/soldier3Glow.png",
                    sayingBubble: ""
                },
                {
                    level8: "/soldier4Glow.png",
                    sayingBubble: "היום נעבור שיעור על טכניקות מסירה"
                }, 
                {
                    level9: "/soldier4Glow.png",
                    sayingBubble: ""
                }, 
                {
                    level10: "/soldier5Glow.png",
                    sayingBubble: ""
                },
                {
                    level11: "/soldier5Glow.png",
                    sayingBubble: "*בבטחון* נעבור הנושאים הבאים"
                }
            ],
            dontPressCharacter: false
        }
    }, 
    computed: {
        currentCharacter() {
            return (
                `level${this.questionCounter}`
                // this.characterImages[this.questionCounter][`level${this.questionCounter}`]
            ); 
        }
    }, 
    methods: {
        updateQuestion() {
            this.dontPressCharacter = true;

            let newPicture = this.characterImages[this.questionCounter][`level${this.questionCounter}`].slice(0, -8);
            this.characterImages[this.questionCounter][`level${this.questionCounter}`] = `${newPicture}.png`;

            let timer = setTimeout (() => {
                this.$emit("update");
            }, 1000);
        }
    }
};

</script>


<template>
    <div id="character">
        <div id="soldier" @click="updateQuestion" :disabled="dontPressCharacter" :class="currentCharacter"></div>
        <!-- <img :src="currentCharacter" alt="soldier" id="soldier" @click="updateQuestion" :disabled="dontPressCharacter"/> -->
    </div>
</template>



<style scoped>
.level0 {
    background-image: url("/soldier1Glow.png");
}

.level1 {
    background-image: url("/soldier1Glow.png");
}

.level2 {
    background-image: url("/soldier1Glow.png");
}

.level3 {
    background-image: url("/soldier2Glow.png");
}

.level4 {
    background-image: url("/soldier2Glow.png");
}

.level5 {
    background-image: url("/soldier2Glow.png");
}

.level6 {
    background-image: url("/soldier3Glow.png");
}

.level7 {
    background-image: url("/soldier3Glow.png");
}

.level8 {
    background-image: url("/soldier4Glow.png");
}

.level9 {
    background-image: url("/soldier4Glow.png");
}

.level10 {
    background-image: url("/soldier5Glow.png");
}

.level11 {
    background-image: url("/soldier5Glow.png");
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