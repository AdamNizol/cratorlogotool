<template>
  <div class="logoDisplayContainer">
    <h1>{{ msg }}</h1>
    <svg :height="size" :width="size">
      <circle class="logoCircle" :cx="size/2" :cy="size/2" :r="(size-outerStrokeWidth)/2" :style="{
        'stroke-width':outerStrokeWidth,
        'stroke-dasharray': 2*Math.PI*(size-outerStrokeWidth)/2,
        'stroke-dashoffset': (-2*Math.PI*(size-outerStrokeWidth)/2)/(360/gap) ,
        /* 'transform': 'rotate(100deg, '+(size/2)+', '+(size/2)+')' */
        'transform': 'rotate('+(angle-90)+'deg)',
        'stroke': primaryCol,
        'stroke-linecap': roundedCaps?'round':'butt',
      }" />
      <circle class="logoCircle" :cx="size/2" :cy="size/2" :r="(innerSize-innerStrokeWidth)/2" :style="{
        'stroke-width':innerStrokeWidth,
        'stroke-dasharray': 2*Math.PI*(innerSize-innerStrokeWidth)/2,
        'stroke-dashoffset': (-2*Math.PI*(innerSize-innerStrokeWidth)/2)/(360/gap),
        /* 'transform': 'rotate(100deg, '+(size/2)+', '+(size/2)+')' */
        'transform': 'rotate('+(angle-90)+'deg)',
        'stroke': secondaryCol,
        'stroke-linecap': roundedCaps?'round':'butt',
      }" />
    </svg>
    <div class="settingContainer">
      <div>
        <label>Primary Color: </label>
        <input type='color' v-model="primaryCol" />
      </div>
      <div>
        <label>Secondary Color: </label>
        <input type='color' v-model="secondaryCol" />
      </div>
      <div>
        <label>Outer Thickness: </label>
        <input type='range' v-model="outerStroke" min="0" max="50"/>
      </div>
      <div>
        <label>Inner Thickness: </label>
        <input type='range' v-model="innerStroke" min="0" max="50" />
      </div>
      <div>
        <label>Angle: </label>
        <input type='range' v-model="angle" min="-10" max="60" />
      </div>
      <div>
        <label>Ring Separation: </label>
        <input type='range' v-model="separation" min="0" max="100" />
      </div>
      <div>
        <label>gap: </label>
        <input type='range' v-model="gap" min="0" max="150" />
      </div>
      <div>
        <label>Rounded End-caps:</label>
        <input type='checkbox' v-model="roundedCaps" min="0" max="150" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LogoDisplay',
  data(){
    return({
      size: 200,
      outerStroke: 10, //percent of size
      innerStroke: 11,
      angle: 17,
      separation: 15,
      primaryCol: '#0b4499',
      secondaryCol: '#7a0e75',
      gap: 90,
      roundedCaps: false,
    })
  },
  props: {
    msg: String
  },
  computed:{
    outerStrokeWidth(){
      return this.size*(this.outerStroke/100)
    },
    innerStrokeWidth(){
      return this.innerSize*(this.innerStroke/100)
    },
    innerSize(){
      return this.size - (2*this.outerStrokeWidth) - (this.size*this.separation/100)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
.logoCircle{
  fill-opacity: 0.0;
  transform-origin: 50% 50%;
}
.settingContainer{
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  width: 200px;
  margin-top: 1em;
  input{
    width: 200px;
    margin-bottom: 0.25em;
  }
  label{
    font-weight: bold;
  }
}
.logoDisplayContainer{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
