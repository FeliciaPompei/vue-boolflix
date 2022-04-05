<template>
    <header class="container-fluid">
        <div class="row text-center p-4 justify-content-between align-items-center">
            <div class="col-2">
                <img class="img-fluid" src="../assets/boolflix-logo.jpg" alt="boolflix logo">
            </div>
            <div class="col-3">
                <div class="input-group mb-3">
                    <span class="input-group-text" id="basic-addon1"><i class="fas fa-magnifying-glass"></i></span>
                    <input type="text" class="form-control" placeholder="Search your favourite film" 
                    v-model.trim="userFilmSearch" 
                    @keydown.enter="$emit('filmSearchInput', userFilmSearch)">
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name:'IndexHeader',
    data : function(){
        return {
            userFilmSearch : '',
        };
    },
}
</script>

<style lang="scss" scoped>



</style>