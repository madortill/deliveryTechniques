<template> 
    <div id="App">
        <img src="./assets/images/madortill.svg" alt="logo" class="logomador" />
        <index v-if="!isMobile"></index>
        <indexMobile v-else></indexMobile>
    </div>
</template>

<script>
import index from "./components/index.vue"
import indexMobile from "./componentsMobile/index.vue"

export default {
    data() {
        return {
            isMobile: true
        }
    },
    components: {index, indexMobile},
    created() {
        if (window.innerWidth >= window.innerHeight) {
            this.isMobile = false;
        } else {
            this.isMobile = true;
        }
    }
}
</script>

<style>
.logomador {
  width: 14vw;
  height: 8vh;
  position: fixed;
  bottom: 2vh;
  right: -3vw;
  z-index: 100;
  max-width: 15vw;
}

</style>