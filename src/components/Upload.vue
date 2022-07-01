<template>
    <div class="menu-element">
        <div class="menu-element flex justify-center mt-6">
            <div class="menu-element mb-3 w-96">
                <label for="formFile" class="menu-element form-label inline-block mb-2 text-gray-700">Upload image</label>
                <input class="menu-element form-control block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none" type="file" v-on:change="manageFile">
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'Upload',

        methods:{
            manageFile: function(e){
                var ghost = new Image();
                ghost.src = 'data:image/gif;base64,R0lGODlhAQABAIAAAAUEBAAAACwAAAAAAQABAAACAkQBADs=';

                const [file] = e.target.files
                if (file) {
                    let newImg = document.createElement('img')
                    newImg.src = URL.createObjectURL(file)
                    newImg.setAttribute('class', 'absolute')
                    newImg.setAttribute('draggable', 'true')
                    newImg.style["top"] = "50%"
                    newImg.style["left"] = "50%"
                    newImg.addEventListener("dragstart",(e)=>{
                            e.dataTransfer.setDragImage(ghost, 0, 0);
                    })
                    newImg.addEventListener("drag", (e)=>{
                        newImg.style["top"] = (e.clientY - newImg.height/2) +"px"
                        newImg.style["left"] = (e.clientX - newImg.width/2) +"px"
                    })
                    newImg.addEventListener("dragend", (e)=>{
                        newImg.style["top"] = (e.clientY - newImg.height/2) +"px"
                        newImg.style["left"] = (e.clientX - newImg.width/2) +"px"

                    })
                    document.querySelector('.content').append(newImg)
                }
            }
        }
    }

</script>
