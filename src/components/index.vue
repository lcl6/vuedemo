/* eslint-disable no-tabs */
<template>
  <div id="indeex" >
    index page
      <div id="new" @click="click">
        新的
      </div>
      <div>
        <button v-on:click="show=!show">toggle</button>
        <!-- slide-fade  fade  bounce-->
        <transition name="bounce">
          <p v-if="show">hello</p>
        </transition>

          <transition
            name="custom-classes-transition"
            enter-active-class="animated tada"
            leave-active-class="animated bounceOutRight"
            >
            <p v-if="show">great</p>
          </transition>
      </div>
      <div class="demo" >
        <button @click="shuffle">flip</button>
        <transition-group name="flip-list" tag="ul">
          <li v-for="item in items" v-bind:key="item">
            {{item}}
          </li>
        </transition-group>
      </div>
      <div id="animated-number-demo">
        <input v-model.number="number" type="number" step="20">
        <p> {{animatedNumber}}</p>
      </div>
    </div>
</template>

<script >
// eslint-disable-next-line no-unused-vars
import _ from 'lodash/lodash'
export default {
  name: 'index',
  data () {
    return {
      show: true,
      items: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      tweenedNumber: 0,
      number: 0
    }
  },
  methods: {
    click: function () {
      // alert('Hello Vue')
      this.$router.push({
        path: '/content',
        query: {
          id: '12'
        }

      })
    },
    shuffle: function () {
      console.log(this.items)
      this.items = [1, 12, 3, 14, 5, 16, 7, 18, 9]
      // this.items = _.shuffle[this.items]
      // console.log(_.shuffle[this.items])
    }
  },
  created: function () {
    console('Hello created')
  },
  computed: {
    // eslint-disable-next-line vue/return-in-computed-property
    animatedNumber: function () {
      return this.tweenedNumber.toFixed(0)
    }
  },
  watch: {
    number: function (newValue) {
      // eslint-disable-next-line no-undef
      TweenLite.to(this.$data, 0.5, { tweenedNumber: newValue })
    }

  }
}

</script>
<style scoped >
#new {
  color: bisque;
  font-size: 15;

}
#indeex {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
/* slide-fade */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
/* bounce */
.bounce-enter-active {
  animation: bounce-in .5s;
}
.bounce-leave-active {
  animation: bounce-in .5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
/* flip */
.flip-list-move {
  transition: transform 1s;
}
</style>
