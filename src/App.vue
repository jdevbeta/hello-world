<template>
  <div>
  <transition 
    mode="out-in"
    enter-active-class="flipInY"
    leave-active-class="flipOutY"
    >
    <component 
      class="animated"
      v-bind:is="this.active.component"
      v-bind:system="this"
      v-bind:active="this.active"
    >
    </component>
    </transition>
    <div id="devPanel">
      {{this.user}}
    </div>
  </div>
</template>


<script>
import sqblLogin from './components/login.vue'
import sqblRegister from './components/register.vue'
import sqblIcons from './components/icons.vue'

export default {
  name: 'app',
  components: {
    'sqblLogin': sqblLogin,
    'sqblRegister':sqblRegister,
    'icon': sqblIcons
  },
  data () {
    return {
      user: {
        first: undefined,
        last: undefined,
        display: undefined,
        alias: undefined
      },
      active: {
        component: 'sqblLogin',
      },
      button: "New User?"
    }
  },
  methods: {

  }
}
</script>

<style>
  div {
    position: relative;
    text-align: center;
  }

  #devPanel {
    position: fixed;
    bottom: 0;
    right: 0;
    height: 20px;
    width: 200px;
    padding: 8px;
    background: #333;
    color: #fff;
  }

  #devPanel:hover {
    height: 250px;
  }


  .hideThis {
    display: none;
  }

  
</style>
