<template>
    <div class="menu-element text-gray-700">
        <div class="menu-element text-2xl font-bold text-center">MENU</div>
        <div class="menu-element flex justify-center mt-6">
            <div class="menu-element mb-3 w-96">
                <div class="menu-element flex flex-col my-8">
                    <label for="file_upload" class="menu-element form-label inline-block mb-1 text-sm">Upload image</label>
                    <input id="file_upload" class="menu-element form-control block w-full px-3 py-1.5 text-base font-normal bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none" type="file" v-on:change="manageFile">
                </div>
                <div class="menu-element my-8">
                    <form class="menu-element flex flex-col">
                        <label for="set_background" class="menu-element form-label inline-block mb-1 text-sm">Set background</label>
                        <input type="text" id="set_background" class="menu-element form-control block w-full px-3 py-1.5 text-base font-normal bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none">
                        <button class="menu-element">set</button>
                    </form>
                </div>
                <div class="menu-element">
                    <form class="menu-element flex flex-col">
                        <label for="create_text" class="menu-element form-label inline-block mb-1 text-sm">Create Text</label>
                        <input type="text" id="create_text" class="menu-element form-control block w-full px-3 py-1.5 text-base font-normal bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none">
                        <button class="menu-element">create</button>
                    </form>
                </div>
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
                    newImg.setAttribute('class', 'absolute drag-element')
                    newImg.setAttribute('draggable', 'true')
                    newImg.style["top"] = "200px"
                    newImg.style["left"] = "200px"
                    newImg.addEventListener("dragstart",(e)=>{
                            e.dataTransfer.setDragImage(ghost, 0, 0);
                    })
                    newImg.addEventListener("drag", (e)=>{
                        if(newImg.classList.contains('edit-ready')) return
                        newImg.style["top"] = (e.clientY - newImg.height/2) +"px"
                        newImg.style["left"] = (e.clientX - newImg.width/2) +"px"
                    })
                    newImg.addEventListener("dragend", (e)=>{
                        if(newImg.classList.contains('edit-ready')) return
                        newImg.style["top"] = (e.clientY - newImg.height/2) +"px"
                        newImg.style["left"] = (e.clientX - newImg.width/2) +"px"

                    })
                    newImg.addEventListener("click", (e)=>{
                        newImg.classList.add('edit-ready')
                    })
                    document.querySelector('.drag-area div').append(newImg)
                }
            }
        }
    }

</script>

<style>
    .drag-element{
        border: 2px solid transparent
    }
    .drag-element.edit-ready{
        border: 2px solid blueviolet
    }
</style>


