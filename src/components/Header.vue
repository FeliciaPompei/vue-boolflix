<template>
    <header class="container-fluid">
        <div class="row text-center p-4 justify-content-between align-items-center">
            <div class="col-6 d-flex my-nav-bar">
                <img id="main-logo" class="me-3" src="../assets/boolflix-logo.jpg" alt="boolflix logo">
                <ul class="navbar-nav flex-row">
                    <li class="nav-item me-2">
                        <a class="nav-link" href="#">Home</a>
                    </li>
                    <li class="nav-item me-2">
                        <a class="nav-link" href="#">movies</a>
                    </li>
                    <li class="nav-item me-2">
                        <a class="nav-link" href="#">tv series</a>
                    </li>
                    <li class="nav-item me-2">
                        <a class="nav-link" href="#">watch later</a>
                    </li>

                </ul>

            </div>
            <div class="col-3 d-flex align-items-center">
                <div class="form">
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="basic-addon1"><i class="fas fa-magnifying-glass"></i></span>
                        <input type="text" class="form-control" placeholder="Search your favourite film" 
                        v-model.trim="userFilmSearch" 
                        @keydown.enter="$emit('filmSearchInput', userFilmSearch)">
                    </div>
                </div>
                <div class="user-profile ms-3">
                    <img class="rounded-circle" src="https://www.pavilionweb.com/wp-content/uploads/2017/03/man-300x300.png" alt="Profile Picture">
                    <h6 class="text-white m-0">UserName</h6>
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

.my-nav-bar{

    #main-logo{
        width: 165px;
    }
    a{
        font-size:1.5rem;
        color:white;
    }
}
.user-profile{
    width: 75px;
    img{
        width:40px;
    }
}


</style>