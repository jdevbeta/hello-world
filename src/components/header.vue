<template>
  <div>
    <button v-on:click="system.toggleForm">
        <icon name="user" dims="20,20"></icon>
      {{system.button}}
    </button>
  </div>
</template>

<script>
import sqblIcons from './icons.vue'

export default {
  name: 'sqbl-header',
  components: {
    icon: sqblIcons,
  },
  props: {
    'system': {
      type: Object,
    }
  },
  data () {
    return {

    }
  }
}
</script>

<style scoped>
  button {
    display: inline-block;
    position: relative;
    margin: 0;
    padding: 5px 5px 2px 5px;
    font-family: 'Roboto Condensed';
    font-size: 20px;
    text-align: center;
    color: #333;
  }
</style>
