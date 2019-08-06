<template>
  <div id="translateFrom">
    <form v-on:submit="formSubmit">
      <input type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容！" />
      <!--<select>
        <option value="en">English</option>
        <option value="en">English</option>
        <option value="en">English</option>
      </select>-->
      <input type="submit" value="翻译" />

    </form>
  </div>
</template>

<script>
  export default {
    name: 'translateFrom',
    data: function ()
    {
      return {
        textToTranslate: "",
      }
    },
    methods:
    {
      formSubmit: function (e)
      {
        //alert(this.textToTranslate);
        this.$emit("formSubmit", this.textToTranslate);
        e.preventDefault();
      }
    }
  }
</script>
<style>
</style>
