<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
  <translate-form @formSubmit="translatetext"></translate-form>
<translate-output v-text="translatedtext"></translate-output>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm';
import translateoutput from './components/TranslateOutPut';
export default {
  name: 'App',
  data:function(){
    return{
      translatedtext:""
    }
  },
  components: {
      "translate-form":TranslateForm,
      "translate-output":translateoutput
  },
  methods:{
    translatetext:function(text,language){
      // alert(text);
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr/translate?key=trnsl.1.1.20190401T065711Z.77e6e57f440be7f9.ab7bc380528a983375b454dd69f985e070402fef&lang=${language}%20&text=${text}`
      ).then((response) => {
        this.translatedtext=response.body.slice(response.body.indexOf('<text>')+6,response.body.indexOf('</text>'));
        console.log(response);
        }).catch((err) => {
          console.log(err)
        });;
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
