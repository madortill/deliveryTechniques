<script>
import Character from './character.vue';
import Questions from './questions.vue';
import endScreen from './endScreen.vue';

export default {
    data() {
        return {
            questionCounter: 0,
            visibleQuestion: true,
        }
    },
    components: { Character, Questions, endScreen }, 
    methods: {
        showQuestion(changed) {
            if (changed === true) {
                this.visibleQuestion = false;
            } else {
                this.visibleQuestion = true;
            }
            this.questionCounter++;
        }
    }
};

</script>




<template>
    <div id="exercize">
        <endScreen v-if="questionCounter === 12"></endScreen>
        <div v-else>
            <Questions @level="showQuestion" :questionCounter="questionCounter" v-show="visibleQuestion"></Questions>
            <Character :questionCounter="questionCounter" id="character" @update="showQuestion" v-show="visibleQuestion === false"></Character>
        </div>
    </div>
</template>



<style scoped>
* {
    height: 100%;
}

#character {
    height: 100vh;
}

#exercize {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    align-items: center;
}
</style>