
<template>
    <div id="content">
        <div>
            <p>  这个是什么什么</p>
        </div>
       </div>
</template>
<script>
export default {
  data () {
    return {
      id: ''
    }
  },
  created () {
    // eslint-disable-next-line no-unused-expressions
    // eslint-disable-next-line no-unused-vars
    var id = this.$route.query.id
    console.log(id)
  }
}
</script>
<style scoped>
#content{
     font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
