<template>
    <div class="wrapperQuestion">
        <h2>{{textQuestion}}</h2>
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
   
    display: table;
    box-sizing: border-box;
    width: 100%;
    height: 100%;
    text-align: center;
}
h2{
    display: table-cell;
    vertical-align: middle;
    font-size: 2em;
}

</style>
