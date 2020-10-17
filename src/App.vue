<template>
  <div id="app">
    <form class="container">
      <h1 class="title">Персональная информация</h1>
      <PersonalInfo />
      <h1 class="title">Информация о месте жительства</h1>
      <AddressInfo />
      <h1 class="title">Документ удостоверяющие личность</h1>
      <DocumentInfo />
      <div class="footer">
        <span v-if="isInvalid" class="errorSelect">{{error}}</span>
        <button v-on:click.prevent="saveClient" class="btn" type="submit">Сохранить клиента</button>
      </div>
    </form>
    <Modal 
      v-bind:show="show"
      v-on:closeModal="hideModal"
    />
  </div>
</template>

<script>
import Modal from './components/Modal'
import PersonalInfo from './components/PersonalInfo'
import AddressInfo from './components/AddressInfo'
import DocumentInfo from './components/DocumentInfo'

export default {
  name: 'App',
  components: {
    PersonalInfo,
    AddressInfo,
    DocumentInfo,
    Modal
  },
  data: () => ({
    show: false,
    isInvalid: false,
    error: 'Введите корректные данные',
    errorNull: 'Заполните поле',
  }),
  methods: {
    saveClient(){
      const inputs= document.querySelectorAll('input');
      const inputItem= document.querySelectorAll('.input-item');
      const clients = document.getElementById('clients'); 
      const clientError = document.querySelector('.clients-error');
      const required = document.querySelectorAll('input[required]');
      let isRequiredError = false;

      inputItem.forEach(item => {
        
        let child = item.querySelector('input');
        let error = item.querySelector('.external-error');

        if (child.required && child.value.length <= 0) { 
          error.style.display = 'block';
          error.textContent = this.errorNull;
          isRequiredError = true;
        }
        else{
          error.style.display = 'none';
          isRequiredError = false;
        }    
      })

      const errors = document.querySelectorAll('.error');
     
      const isValid = [...clients].some(element => element.selected);
      if (!isValid || errors.length !== 0 || isRequiredError) {
        clientError.style.display = 'block';
        clientError.textContent = this.errorNull;
        return this.isInvalid = true;
      }
      this.show = true;
      this.isInvalid = false;
      clientError.style.display = 'none';
      inputs.forEach(item =>{
        item.value ='';
      });
    },
    hideModal(){
      this.show = false;
    }
  }
}
</script>

<style>
  .footer{
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }

  .errorSelect{
    color: red;
    margin-right: 30px;
    font-size: 20px;
  }

  .btn{
    height: 50px;
    width: 200px;
    text-align: center;
    border: 1px solid white;
    padding: 10px;
    transition: 0.5s linear;
    cursor: pointer;
    color: white;
    background-color: transparent;
    font-size: 17px;
    outline: none;
  }

  .btn:hover{
    background-color: white;
    color: #3FB0C5;
  }

  @media screen and (max-width: 500px){
    .footer{
      flex-direction: column;
    } 
    .errorSelect{
      margin-right: 0; 
    }
    .btn{
      margin-top: 30px;
    }
  }
  @import './css/reset.css';
  @import './css/style.css';
</style>
