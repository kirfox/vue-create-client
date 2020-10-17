<template>
  <div class="input-item">
    <label v-bind:for="id">
      {{label}}
      <span v-if="required" class='required'>*</span>
    </label>
    <input 
      v-model= 'inputValue'
      v-on:input= "validate"
      class= 'container__text' 
      type="text" 
      v-bind:placeholder="placeholder" 
      v-bind:id="id"
      v-bind:required="required"
    >
    <span v-if="isInvalid" class="error">{{error}}</span>
    <span class="external-error"></span>
  </div>
</template>

<script>
  export default {
    name: 'InputItem',
    props: {
      label: String,
      placeholder: String,
      required: Boolean,
      id: String,
      rules: {
        type: Array,
        default: () => [],
      }
    },
    data: () => ({
      inputValue: null,
      error: '',
      isInvalid: false
    }),
    methods: {
      validate(){
        this.isInvalid = false;
        if (!this.required && this.inputValue.length <= 0) {
          return;
        }
        if (this.required && this.inputValue.length <= 0) {
          this.error = `Поле ${this.label} обязательное`;
          this.isInvalid = true;
          return;
        }
        if (this.inputValue.length > 0) {
          for (let i = 0; i < this.rules.length; i++) {
            const rule = this.rules[i];
            if (!rule.regExp.test(this.inputValue)) {
              this.error = rule.errorText;
              this.isInvalid = true;
              break;
            }
            else{
              this.isInvalid = false;
            }
          }   
        }
      }
    },
  }
  
</script>

<style scoped>
  div{
    display: flex;
    flex-direction: column;
  }
  .error{
    color: red;
  }
  .external-error{
    display: none;
    color: red;
  }
</style>

