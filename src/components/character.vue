<script>
export default {
    props: ["questionCounter"],
    data() {
        return {
            characterImages: [
                {
                    level0: "src/assets/images/soldier1Glow.png",
                    sayingBubble: "אוי, אני לא יודעת מה להגיד להם",
                    changes: true
                }, 
                {
                    level1: "src/assets/images/soldier1Glow.png"
                },
                {
                    level2: "src/assets/images/soldier1Glow.png"
                }, 
                {
                    level3: "./@/assets/images/soldier2Glow.png"
                },
                {
                    level4: "./@/assets/images/soldier2Glow.png"
                }, 
                {
                    level6: "./@/assets/images/soldier3Glow.png"
                }, 
                {
                    level7: "./@/assets/images/soldier3Glow.png"
                },
                {
                    level8: "./@/assets/images/soldier3Glow.png"
                }, 
                {
                    level9: "./@/assets/images/soldier4Glow.png"
                }, 
                {
                    level10: "./@/assets/images/soldier4Glow.png"
                }, 
                {
                    level11: "./@/assets/images/soldier4Glow.png"
                }
            ],
            dontPressCharacter: false
        }
    }, 
    computed: {
        currentCharacter() {
            console.log(this.characterImages[this.questionCounter][`level${this.questionCounter}`])
            return (
                // `level${this.questionCounter}`
                this.characterImages[this.questionCounter][`level${this.questionCounter}`]
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
        <!-- <div id="soldier" @click="updateQuestion" :disabled="dontPressCharacter" :class="currentCharacter"></div> -->
        <img :src="currentCharacter" alt="soldier" id="soldier" @click="updateQuestion" :disabled="dontPressCharacter"/>
    </div>
</template>



<style scoped>
.level0 {
    background-image: url("@/assets/images/soldier1Glow.png");
}

.level1 {
    background-image: url("@/assets/images/soldier1Glow.png");
}

.level2 {
    background-image: url("@/assets/images/soldier1Glow.png");
}

.level3 {
    background-image: url("@/assets/images/soldier2Glow.png");
}

.level4 {
    background-image: url("@/assets/images/soldier2Glow.png");
}

.level5 {
    background-image: url("@/assets/images/soldier2Glow.png");
}

.level6 {
    background-image: url("./@/assets/images/soldier3Glow.png");
}

.level7 {
    background-image: url("@/assets/images/soldier3Glow.png");
}

.level8 {
    background-image: url("@/assets/images/soldier3Glow.png");
}

.level9 {
    background-image: url("@/assets/images/soldier4Glow.png");
}

.level9 {
    background-image: url("@/assets/images/soldier4Glow.png");
}

.level10 {
    background-image: url("@/assets/images/soldier4Glow.png");
}

.level11 {
    background-image: url("@/assets/images/soldier4Glow.png");
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
    width: 60vw;
    position: relative;
    top: 15vh;
    height: 75vh;
}
</style>