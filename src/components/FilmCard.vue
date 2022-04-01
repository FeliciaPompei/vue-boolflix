<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title"> {{film.title}} </h5>
            <p class="card-text"> {{film.original_title}} </p>
            <p class="card-text"> {{film.original_language} </p>
            <p class="card-text"> {{film.vote_average} </p>
        </div>
    </div>
</template>

<script>
export default {
    name:'FilmCard',
    props : ['film']
}
</script>

<style lang="scss" scoped>

</style>