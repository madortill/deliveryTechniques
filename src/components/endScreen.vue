<template>
    <div id="endScreen">
        <div id="message"><b>כל הכבוד!</b></div>
        <div class="message">סיימת את הלומדה בהצלחה!</div>
        <img src="@/assets/images/table.png" class="table" alt="table" />
    </div>
</template>



<style scoped>
#endScreen {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#message{
    margin-top: 10vh;
    padding-top: 5vh;
    font-size: 7vh;
    text-align: center;
    direction: rtl;
    color: #185f64;
}

.message{
    font-size: 5vh;
    text-align: center;
    direction: rtl;
}
.table {
    width: 40vw;
    height: 30vh;
}
</style>