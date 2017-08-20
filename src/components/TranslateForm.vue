<template>
  <div id="translateForm" class="row">
  	<div class="col-md-6 col-md-offset-3">
	  	<form id='transForm' class='form-inline well' v-on:submit="formSubmit">
			<input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word">
			<select class="form-control" v-model='language'>
				<option value="it">Italian</option>
				<option value="	la">Latin</option>
				<option value="	tg">Tajik</option>
				<option value="fr">French</option>
			</select>
			<input type="submit" class="btn btn-primary" value="Translate">		
	  	</form>
  	</div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
  	return{
  		textToTranslate:"",
  		language:''
  	}
  },
  created(){
  	this.language='it';
  },
  methods:{
  	formSubmit(e){
  		this.$emit('formSubmit',this.textToTranslate,this.language);
  		e.preventDefault();
  	}
  }

}
</script>

<style>
	#transForm{
		border-radius:10px ;
		border: 1px #ccc solid;
	}	
</style>
