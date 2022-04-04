<template>
    <div class="loader-wrapper d-flex justify-content-center align-items-center">
        <div class="loader d-flex justify-content-center">
            <div class="loader-container">
                <div class="loader-film">
                    <img class="loader-film-img" src="https://www.dropbox.com/s/o4p5i3nfw92rhfz/film.png?raw=1" alt="" />
                    <img class="loader-film-img" src="https://www.dropbox.com/s/o4p5i3nfw92rhfz/film.png?raw=1" alt="" />
                </div>
                <img class="loader-camera" src="https://www.dropbox.com/s/348z6yvtt9hbos2/camera.png?raw=1" alt="" />
            </div>
        </div>
        <h1 class="text-warning">Search for your favourite film or TV series</h1>
    </div>
</template>

<script>
export default {
    name : 'LoaderIndex'
}
</script>

<style lang="scss" scoped>
.loader-wrapper {
    width: 100vw;
    height: 80vh;
}

@keyframes rotate {
from {
    transform: rotate(0);
}

to {
    transform: rotate(360deg);
}
}

.loader-container {
    position: relative;
    display: flex;
    align-items: center;
    height: 40px;
}

.loader-film {
    position: absolute;
    top: -30px;
    left: 0;
    display: flex;
}

.loader-film-img {
    animation: rotate 1.5s linear infinite;
}

</style>