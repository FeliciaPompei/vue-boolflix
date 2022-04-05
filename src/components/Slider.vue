<template>
    <div class="slider-container" @mouseleave = "autoPlay" @mouseover = "stopPlay">
        <div class="my-carousel-images">
            <div v-for="(element, index) in sliderImg" :key="index"> 
                <!-- Add v-for -->
                <div class= "img-wrapper" :class="(index == sliderIndex) ? 'd-block' : 'd-none' ">
                    <img class="card-img-top img-fluid"  :src="`http://image.tmdb.org/t/p/w185${element.poster_path}`" :alt="element.original_title">
                </div>
            </div>
            <div class="buttons text-white">
                <div class="my-previous position-absolute" @click = "previousSlide">
                    <span class="my-prev-hook">&larr;</span>
                </div>
                <div class="my-next position-absolute" @click = "nextSlide">
                    <span class="my-next-hook">&rarr;</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SliderIndex',
    props : ['sliderImg'],
    data(){
        return {
            isInAutoScroll : null,
            sliderIndex : 0
        }
    },
    methods :{
        nextSlide : function (){
            if(this.sliderIndex == (this.sliderImg.length -1)){
                this.sliderIndex = 0;
            } else {
                this.sliderIndex++;
            }
        },
        previousSlide : function (){
            if(this.sliderIndex == 0){
                this.sliderIndex = this.sliderImg.length -1;
            } else {
                this.sliderIndex--;
            }
        },
        autoPlay : function(){
            this.isInAutoScroll = setInterval(this.nextSlide, 3000);
        },
        stopPlay: function(){
            this.isInAutoScroll = clearInterval(this.isInAutoScroll);
            this.isInAutoScroll = null;
        },
    }
}
</script>

<style lang="scss" scoped>
.slider-container {
    width:100%;
    height:60vh;
    background-color: green;
    position:relative;
    img{
        width:100%;
        height:60vh;;
        object-fit: cover;
    }
    .my-previous, .my-next{
        position: absolute;
        top:50%;
        transform: translateY(-50%);
        cursor: pointer;
        border-radius: 50%;
        padding: 2rem;
        background-color:black;
    }
    .my-previous{
        left: 2rem;
    }
    .my-next{
        right: 2rem;
    }
}
</style>