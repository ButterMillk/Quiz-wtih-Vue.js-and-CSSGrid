<template>
    <div class="wrapperInformations">
        <p>Punkty: {{ gamer.score }}</p>
        <p>Liczba szans: {{ gamer.opportunities }}</p>
    </div>
</template>

<script>
export default {
    name: 'Informations',

    props:{
        gamer: Object,
    }
}
</script>

<style scoped>
.wrapperInformations{
    box-sizing: border-box;
    padding: 10px;
}

</style>