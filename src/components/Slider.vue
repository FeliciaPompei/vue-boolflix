<template>
    <div class="slider-container mb-5" @mouseleave = "autoPlay" @mouseover = "stopPlay">
        <div class="my-carousel-images">
            <div v-for="(element, index) in sliderImg" :key="index"> 
                <!-- Add v-for -->
                <div class= "img-wrapper" :class="(index == sliderIndex) ? 'd-block' : 'd-none' ">
                    <img class="card-img-top img-fluid"  :src="`http://image.tmdb.org/t/p/w185${element.backdrop_path}`" :alt="element.original_title">
                    <div class="img-description">
                        <h1> {{element.title}} </h1>
                    </div>
                </div>
            </div>
            <div class="buttons text-white">
                <div class="my-previous position-absolute" @click = "previousSlide">
                    <span class="my-prev-hook"><i class="fa-solid fa-chevron-left"></i></span>
                </div>
                <div class="my-next position-absolute" @click = "nextSlide">
                    <span class="my-next-hook"><i class="fa-solid fa-chevron-right"></i></span>
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
        height:60vh;;
        object-fit: cover;
    }
    .img-description{
        position:absolute;
        top: 50%;
        left:50%;
        transform: translate(-50%, -50%);
        text-align:centeR;
        h1{
            font-size: 4rem;
            color:white;
            background-color: rgba($color: #000000, $alpha: 0.4);
            border-radius: 2rem;
            padding: 1rem;
        }
    }
    .my-previous, .my-next{
        position: absolute;
        top:50%;
        transform: translateY(-50%);
        cursor: pointer;
        padding: 0.5rem 1rem;
        font-size: 1.5rem;
    }
    .my-previous{
        left: 2rem;
    }
    .my-next{
        right: 2rem;
    }
}
</style>