<template>
  <div class="text-center" id="app">
    <div>
      <img src="./assets/new-logo-big.png" />
    </div>
    <h1>Vatcher Translator</h1>
    <h5>Powered by Vue.js</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import translateForm from './components/translateForm'
import translateOutput from './components/translateOutput'
export default {
  name: 'app',
  components:{
    translateForm,
    translateOutput
  },
  data: function(){
    return {
      translatedText: ''
    }
  },
  methods:{
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170702T230848Z.b7255621c0b73851.532918bee6944cc106f28d8e4ac0f46847d61e81&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
  body{ background-color: #272727;
        color: white;
        margin: 20px;
        font-family: 'Arial', sans-serif;
        font-size: 2em;
        margin: 30px;
        }
        

  .text-center{
    text-align: center;
  }

</style>
