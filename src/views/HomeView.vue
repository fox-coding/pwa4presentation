<template>
  <div class="home left-0 top-0 h-screen overflow-hidden h-screen w-screen">
    <div class="drag-area w-full h-full overflow-x-scroll">
      <div style="background: linear-gradient(183deg, rgb(98, 174, 239) 15%, rgb(152, 195, 121) 85%)" class="scroll-container relative w-[1000%] h-screen">

      </div>
    </div>
    <ArrowNavigation />
  </div>
</template>

<script>
// @ is an alias to /src
import ArrowNavigation from '@/components/ArrowNavigation.vue'

export default {
  name: "HomeView",
  components: {
    ArrowNavigation
  },

  props:{
    name: ""
  },

  data() {
    return {
    };
  },

  methods: {
  },
};
</script>