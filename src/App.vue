<template>
  <div class="text-center" id="app">
    <div>
      <svg id="Layer" data-name="Layer 1" width="300px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 279.21 176.38"><defs><linearGradient id="linear-gradient" x1="229.5" y1="426.98" x2="350.9" y2="426.98" gradientTransform="translate(-224.67 464.81) rotate(-60)" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#2affcc"/><stop offset="1" stop-color="#00276a"/></linearGradient><linearGradient id="linear-gradient-2" x1="302.33" y1="426.98" x2="423.73" y2="426.98" gradientTransform="translate(174.78 954.86) rotate(-120)" xlink:href="#linear-gradient"/><linearGradient id="linear-gradient-3" x1="414.6" y1="483.31" x2="508.7" y2="483.31" gradientTransform="translate(303.5 -166.08) rotate(30)" xlink:href="#linear-gradient"/><linearGradient id="linear-gradient-4" x1="414.6" y1="444.08" x2="508.7" y2="444.08" gradientTransform="translate(-160.19 290.32) rotate(-30)" xlink:href="#linear-gradient"/></defs><title>V-translate-logo</title><rect class="cls-1" x="193.09" y="402.7" width="194.23" height="48.56" rx="24.28" ry="24.28" transform="translate(285.37 -377.45) rotate(60)"/><rect class="cls-2" x="265.92" y="402.7" width="194.23" height="48.56" rx="24.28" ry="24.28" transform="translate(684.82 -13.55) rotate(120)"/><rect class="cls-3" x="409.35" y="470.23" width="104.61" height="26.15" rx="13.08" ry="13.08" transform="translate(-409.3 -44.04) rotate(-30)"/><rect class="cls-4" x="409.35" y="431" width="104.61" height="26.15" rx="13.08" ry="13.08" transform="translate(54.39 -510.95) rotate(30)"/></svg>
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
        font-size: 2em;}

  .text-center{
    text-align: center;
  }

</style>
