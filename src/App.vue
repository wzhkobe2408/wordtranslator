<template>
  <div class="text-center" id="app">
    <h1 >Word Translator</h1>
    <h5>Power by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components:{
        TranslateForm,
        TranslateOutput
  },
  data: function(){
      return{
        translatedText:""
      }
    },

  methods:{
    translateText:function(text,language){
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170813T112531Z.091ed5616aca5872.071270861b5baf3bce606361c7a42c637caa0273&lang='+language+'&text='+text)
          .then((response) => {
            this.translatedText=response.body.text[0];
          });
      }
    }
  }
</script>
  
<style>
body {
  background: #fefefe;
}

.text-center{
  margin-top: 160px;
}
</style>
