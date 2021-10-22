<template>
  <div id="app">
    <Test v-bind:class = "[colors[0], {Light:redIsLight}]" msg="Привет Тема!"/>
    <Test v-bind:class = "[colors[1], {Light:yellowIsLight}]" msg="Смотри чо могу!"/>
    <Test v-bind:class = "[colors[2], {Light:greenIsLight}]" msg="Опана! 3 цвета!"/>
    <button v-on:click="changeColor">Изменить цвет!</button>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Test from './components/Test.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Test
  },

  data () {
    return {
      colors: [
        'red',
        'yellow',
        'green'
      ],
      redIsLight: true,
      yellowIsLight: false,
      greenIsLight: false,
      countColors: 1,
      countDown: 10
    }
  },
  methods: {
    countDownTimer: function () {
      if (this.countDown > 0) {
        setTimeout(() => {
          this.countDown -= 1
          this.countDownTimer()
        }, 1000)
        console.log('Таймер кончился')
        this.yellowIsLight = !this.yellowIsLight
      }
    },
    yellowLightOn: function () {
      console.log('Желтый')
      this.greenIsLight = false
      this.redIsLight = false
      this.yellowIsLight = true
      this.countDownTimer()
    },
    changeColor: function () {
      console.log(this.countColors)
      switch (this.countColors) {
        case 0:
          console.log('Красный!')
          this.yellowLightOn()
          this.redIsLight = !this.redIsLight
          this.countColors++
          break
        case 1:
          console.log('Зеленый')
          this.yellowLightOn()
          this.countColors = 0
          this.greenIsLight = !this.greenIsLight

          break
      }
    }
  }
}
</script>

<style>
  .red{
    background-color: red;
    opacity: 0.3;
  }
  .yellow{
    background-color: yellow;
    opacity: 0.3;
  }
  .green{
    background-color: green;
    opacity: 0.3;
  }
  .Light{
    opacity: 1;
  }
</style>
