<template>
    <header class="container-fluid">
        <div class="row text-center p-4 justify-content-center">
            <div class="col-4">
                <div class="input-group mb-3">
                    <span class="input-group-text" id="basic-addon1"></span>
                    <input type="text" class="form-control" placeholder="Search your favourite film" 
                    v-model="userFilmSearch" 
                    @keydown.enter="$emit('filmSearchInput', userFilmSearch)">
                    <button class="btn btn-info" 
                    @click="$emit('filmSearchInput', userFilmSearch)">
                    Search
                    </button>
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

header{
    height: 100px;
    background-color: paleturquoise;
}

</style>