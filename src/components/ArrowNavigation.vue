<template>
    <div class="absolute bottom-6 flex left-1/2">
        <div class="w-10 h-10 bg-red-500 mx-6" @click="slideLeft"></div>
        <div class="w-10 h-10 bg-red-500 mx-6" @click="slideRight"></div>
    </div>
</template>

<script>

export default({
    props:{
        activeSlide: 0
    },

    methods:{
        slideLeft:()=>{
            var target = document.querySelector('.drag-area')
            var sLeft = target.scrollLeft;
            var maxWidth = window.innerWidth
            console.log(sLeft)
            target.scrollTo({
                top: 0,
                left: sLeft - maxWidth,
                behavior: 'smooth'
            });
        },
        slideRight:()=>{
            var target = document.querySelector('.drag-area')
            var sLeft = target.scrollLeft;
            var maxWidth = window.innerWidth
            target.scrollTo({
                top: 0,
                left: sLeft + maxWidth,
                behavior: 'smooth'
            });
        }
    }
})
</script>
