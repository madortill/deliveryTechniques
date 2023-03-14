<script>
export default {
    props: ["questionCounter"],
    data() {
        return {
            characterImages: [
                {
                    level0: "/public/soldier1Glow.png",
                    sayingBubble: ""
                },
                {
                    level1: "/public/soldier1Glow.png",
                    sayingBubble: "*לוחשת*"
                },
                {
                    level2: "/public/soldier1Glow.png",
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
        <img :src="currentCharacter" alt="soldier" id="soldier" @click="updateQuestion" :disabled="dontPressCharacter"/>
        <div id="speakingBubble">{{ this.characterImages[this.questionCounter]["sayingBubble"] }}</div>
    </div>
</template>



<style scoped>
#character {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    align-content: center;
    align-items: center;
}

#soldier {
    position: relative;
    top: 15vh;
    height: 75vh;
}

#speakingBubble {
    width: 10vw;
    position: relative;
    bottom: 58vh;
    right: 9vw;
}
</style>