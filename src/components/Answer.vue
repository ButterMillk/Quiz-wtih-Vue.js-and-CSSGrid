<template>
    <div class="wrapperAnswer">
        <p>{{ textAnswer.answer }}</p>
    </div>
</template>

<script>
export default {
    name: 'Answer',
    props:{
        textAnswer: String,
    }
}
</script>

<style scoped>
.wrapperAnswer{
    box-sizing: border-box;
    width: 25vw;
    background-color: #FFFF99;
    text-align: center;
    display: inline-block;
    margin: 0;
    padding: 0;
}

</style>