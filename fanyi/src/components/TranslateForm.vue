<template>
  <div class="row" id="translateForm">
  <div class="col-md-6 offset-md-3">
    <form id="transForm" class="well form-inline" @submit="formSubmit">
      <input class="form-control"type="text" v-model="textToTranslate" placeholder="请输入要翻译的内容">
      <select class="form-control" v-model="language">
        <option value="en">EngLish</option>
        <option value="ru">Russian</option>
        <option value="ko">棒子</option>
        <option value="it">意大利</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">
    </form>
  </div>
</div>
</template>

<script>


export default {
  name: 'translateForm',
  data:function(){
    return{
      textToTranslate:"",
      language:""
    }
  },
  methods:{
    formSubmit:function(e){
      this.$emit("formSubmit",this.textToTranslate,this.language);

      e.preventDefault();
      // alert(this.textToTranslate)
    }
  },
  created:function(){
    this.language="en";
  }
}
</script>
<style>
#transForm{
  border: 1px #ccc solid;
  border-radius: 10px;
}
</style>

