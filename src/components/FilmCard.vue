<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{filmItem.original_title}} </h5>
        <p class="card-text"> {{filmItem.original_title}} </p>
        <p class="card-text"> {{filmItem.original_language}} </p>
        <p class="card-text"> {{filmItem.vote_average}} </p>
        </div>
    </div>
</template>

<script>
export default {
    name:'FilmCard',
    props : ['filmItem']
}
</script>

<style lang="scss" scoped>
.card{
    background-color:palegreen;
    width:200px;
}
</style>