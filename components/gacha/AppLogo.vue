<template>
  <div class="container">
    <div>
      <h1>
        ラーメンを購入
      </h1>

      <div class="vending">
        <img src="/ticket_vending_machine.jpg" />
      </div>

      <div @click="getItem()" class="button">
        <img src="~assets/purchase.png" alt="">
      </div>
      <p>のこり{{ $store.state.counter }} マシマシ</p>
      <p>10マシマシ消費します</p>
    </div>

    <div class="result" v-if="result" @click="closeResult()">
      <h1>GET</h1>
      <div class="result-item">
        <p class="name">{{ramen["name"]}}</p>
        <p class="menu">{{ramen["menu"]}}</p>
        <img v-bind:src="ramen['img']"/>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
  data () {
    return {
      ramen: {
        name: null,
        menu: null
      },
      result: false
    }
  },
  methods: {
    closeResult: function() {
      self.result = false
    },
    getItem: function() {
        self = this
        fetch('https://api.myjson.com/bins/d3xia')
          .then(data => data.json())
          .then(data => {
            const ramen = data[Math.floor(Math.random() * data.length)]
            ramen.menu = 'ラーメン'
            console.log(ramen)
            self.name = ramen.name
            self.ramen = ramen
            self.result = true

            self.$store.commit('decrement')
            self.$store.commit('addCollection', ramen)
          })
      }
  }
}
</script>

<style>
.main {
  padding: 10px;
  text-align: center;
  position: relative;
}

ul {
  list-style: none;
}

.button img{
 width: 250px;
}

.result {
  top: 0px;
  left: 0ppx;
  position: absolute;
  width: 100%;
  height: 100%;
  background: rgba(10, 10, 10, 0.8);
  justify-content: center;

  color: rgba(200, 200, 200, 1);
}

.result h1{
 font-size: 40pt;
}

.result-item {
  margin-top: 30px;
}

.result-item img {
  height: 100px;
}

.vending img{
  height: 300px;
}
</style>
