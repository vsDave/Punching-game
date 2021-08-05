<template>
  <div id="app">
    <!-- <h1>{{ age }}</h1>

    <button @click="add">age</button>
    <h1 v-on:dblclick.once="add">{{ age }}</h1>
    <button @dblclick.once="discard">delete</button>
    <div id="canvas" v-on:mouseover="updateXY">{{ X }},{{ Y }}</div>
    <input type="text" v-model="salary" />
    <span>{{ salary }}</span> -->

    <!-- bag image  -->
    <div class="bag">
      <img v-if="!ended" src="@/assets/bag.png" alt="" />
      <img v-else src="@/assets/bag-burst.png" />
    </div>
    <!-- bag health -->
    <div class="bag-health">
      <div :style="{ width: health + 'px' }"></div>
    </div>
    <h1>{{ health }}%</h1>
    <!-- game control -->
    <div class="controls">
      <button @click="punch" v-show="!ended">Punch</button>
      <button @click="restart">Restart</button>
    </div>
  </div>
</template>

<script>
/*export default allows us to export as
javascript module
-- events means mouseover , on click which can be bind with v-on
-- EVENT MODIFIER are .once .prevent(prevents default behaviour)
-- two way data binding with v-model
*/
export default {
  data() {
    return {
      health: 200,
      ended: false,
    }
  },
  methods: {
    punch() {
      this.health -= 10
      if (this.health <= 0) {
        this.ended = true
      }
    },
    restart() {
      this.health = 200
      this.ended = false
    },
  },
  computed: {},
}
</script>

<style>
h1 {
  text-align: center;
}
.main {
  display: flex;
  justify-content: center;
  gap: 100px;
  flex-direction: column;
}
.bag {
  width: 200px;
  height: 50px;
  margin: 0 auto;
  background: url() center no-repeat;
  background-size: 80%;
}
.bag img {
  width: 100%;
  height: max-content;
}
/* 
.bag.burst {
  background-image: url(/assets/bag-burst.png);
} */

.bag-health {
  width: 200px;
  border: 2px solid #000;
  margin-left: auto;
  margin-right: auto;
  margin-top: 500px;
}

.bag-health div {
  height: 20px;
  background: rgb(209, 72, 63);
}
.controls {
  width: 120px;
  margin: 50px auto;
}
.controls button {
  background: chocolate;
}
</style>
