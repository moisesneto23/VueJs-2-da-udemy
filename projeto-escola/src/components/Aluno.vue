<template>
    <div>
        <h1> {{qualquercoisa}} </h1>
        <input type="text" placeholder="Nome do Aluno" v-model="qualquercoisa">
    </div>
</template>
<script>
export default {
    data() {//aqui é necessario exportar algo e essa data pode ser qualquer coisa
        return {
           qualquercoisa: 'Aluno',
        }
    },

}
</script>
<style scoped>

</style>