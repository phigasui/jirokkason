<template>
  <section class="container">
    <app-logo/>
  </section>
</template>

<script>
import AppLogo from '~/components/charge/AppLogo.vue'

export default {
  data () {
    return {
      msg: 0
    }
  },
  components: {
    AppLogo
  },
  methods: {
    incliment: function (event) {
      self = this
      self.msg += 1
    }
  }
}

</script>

<style>
* {
   -ms-user-select: none; /* IE 10+ */
   -moz-user-select: -moz-none;
   -khtml-user-select: none;
   -webkit-user-select: none;
   user-select: none;
}
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
