<template>
    <div class="wrapperQuestion">
        <p >Tutaj jest pytanie: {{textQuestion}}</p>
    </div>
</template>

<script>
export default {
    name: 'Question',
    props:{
      textQuestion: String,

    }
}
</script>

<style scoped>
.wrapperQuestion{
    box-sizing: border-box;
    text-align: center;
}

</style>
