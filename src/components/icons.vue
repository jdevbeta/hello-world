<template>
    <!-- <span class="sqbl-icon">
        <img :src="dirPath" :class="this.name"  />
    </span>
     -->
    <svg :style="iconDimensions" class="sqbl-icon">
        <use :xlink:href='fontPath'></use>
    </svg>
</template>

<script>
export default {
  name: 'icons',
  props: {
      name:{
          type: String,
          default: 'square'
      },
      dims:{
          type: Number | String,
          default: '50,50'
      },
      from:{
          type: String,
          default: 'solid'
      },
    },
  computed: {
    dirPath: function(){
        return './src/assets/'+this.from+'/'+this.name+'.svg'
    },
    fontPath: function(){
        return './src/assets/fa-'+this.from+'.svg#'+this.name
    },
    iconDimensions: function(){
        console.log(typeof this.dims+'|'+this.dims)
        if(typeof this.dims === 'string'){
            var dimension = this.dims.split(',');
            var heightDim = dimension[1] || dimension[0];
             return {
                width: dimension[0]+"px",
                height: heightDim+"px"
            }
        }
    }
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
    span, img {
        float: left;
    }

    span {
        display: inline;
        box-sizing: border-box;
    }

    img {
        box-sizing: border-box;
        height: 100%;
        width: 100%;
    }

    svg {
        fill: currentColor;
    }
</style>
