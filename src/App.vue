<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 / 易用 / 便捷</h5>
    <TranslateFrom v-on:formSubmit="translateText" />
    <TranslateOutput v-text="translatedText" />
  </div>
</template>
<script>
  import HelloWorld from './components/HelloWorld'
  import TranslateFrom from './components/TranslateFrom'
  import TranslateOutput from './components/TranslateOutput'

  export default {
    name: 'App',
    components: {
      HelloWorld, TranslateFrom, TranslateOutput
    },
    data: function ()
    {
      return {

        translatedText: ''
      }
    },




    methods: {
      translateText: function (text)
      {
        var url = 'api/translate?&doctype=json&type=AUTO&i=' + text;
        this.$http.get(url).then((result) =>
        {
          var a = result.body.translateResult[0][0].tgt;
          this.translatedText = a;
        });

      }

    }
  }
</script>

<style>

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
