<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="my_target"></div>
    <div><button @click="text_noto">NOTO</button> <button @click="text_mincho">MINCHO</button></div>
  </div>
</template>

<script>
export default {
  name: 'Composite',
  mounted () {
    this.$Jimp.read('http://localhost:8080/static/images/example_01.jpg').then(function (lenna) {
      this.originalImage = lenna.clone()
      this.srcImage = lenna
      lenna.resize(700, 468)
        .getBase64(this.$Jimp.MIME_PNG, function (err, src) {
          this.imgNode = document.createElement('img')
          this.imgNode.setAttribute('src', src)

          let target = document.getElementById('my_target')
          target.appendChild(this.imgNode)

          err && console.log(err)
        }.bind(this))
    }.bind(this)).catch(function (err) {
      console.error(err)
    })
  },
  methods: {
    text_noto: function () {
      this.$Jimp.read('http://localhost:8080/static/images/notosanscjkjp_black_700x468.png').then(function (text) {
        this.srcImage = this.originalImage.clone()
        this.srcImage.resize(700, 468)
          .composite(text, 0, 0)
          .getBase64(this.$Jimp.MIME_PNG, function (err, src) {
            this.imgNode.setAttribute('src', src)
            err && console.log(err)
          }.bind(this))
      }.bind(this)).catch(function (err) {
        console.error(err)
      })
    },
    text_mincho: function () {
      this.$Jimp.read('http://localhost:8080/static/images/genkai_mincho_700x468.png').then(function (text) {
        this.srcImage = this.originalImage.clone()
        this.srcImage.resize(700, 468)
          .composite(text, 0, 0)
          .getBase64(this.$Jimp.MIME_PNG, function (err, src) {
            this.imgNode.setAttribute('src', src)
            err && console.log(err)
          }.bind(this))
      }.bind(this)).catch(function (err) {
        console.error(err)
      })
    }
  },
  data: function () {
    return {
      msg: 'Welcome to Your Vue.js App',
      originalImage: null,
      srcImage: null,
      overlayImage: null,
      imgNode: null
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
