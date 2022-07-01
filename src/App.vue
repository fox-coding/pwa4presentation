<template>
  <menu :class="`${showMenu ? 'translate-x-[0]' : 'translate-x-[-405px]'}`" class="transition-transform delay-150 menu-element w-84 h-full bg-zinc-200 shadow-md p-4 fixed z-10">
    <nav class="text-center">
    </nav>
    <Upload />
  </menu>
  <div class="content w-screen h-screen text-center p-10 relative">
      <router-view/>
  </div>
</template>

<script>
// @ is an alias to /src
import Upload from '@/components/Upload.vue'

export default {
  components: {
    Upload
  },

  data(){
    return{
      showMenu: false
    }
  },

  created: function () {
    document.addEventListener('mousemove',(e)=>{
      var x = e.clientX
      if(x < 20){
        this.showMenu = true
      }else{
        if(!e.target.classList.contains('menu-element')){
          this.showMenu = false
        }
      }
    })
  },
}
</script>
