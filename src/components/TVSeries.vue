<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{seriesItem.name}} </h5>
        <p class="card-text"> {{seriesItem.original_name}} </p>
        <p class="card-text"> {{seriesItem.original_language}} </p>
        <p class="card-text"> {{seriesItem.vote_average}} </p>
        </div>
    </div>
</template>

<script>
export default {
    name:'TVSeries',
    props : ['seriesItem']
}
</script>

<style lang="scss" scoped>
.card{
    background-color:paleturquoise;
    width:200px;
}
</style>