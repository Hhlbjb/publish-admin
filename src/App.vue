<template>
  <div id="app">
    <router-view/>
  </div>
</template>
<script>
export default {
  name: 'App',
  data () {
    return {
      num: 1
    }
  },
  methods: {
    handleChange (value) {
      console.log(value)
    }
  },
  created () {

  }
}
</script>
<style lang = "less"></style>
