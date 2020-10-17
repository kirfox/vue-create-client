<template>
<div v-if="show" class="wrapper">
  <div class="modal">
    <span class="modal-text">Пользователь сохранен!</span>  
    <button v-on:click="close" class="close">ОК</button>
  </div>
</div>
</template>

<script>
  export default {
    name: "Modal",
    data: () =>({

    }),
    props: {
      show: Boolean,
    },
    methods: {
      close(){
        this.$emit('closeModal');
      }
    }
  }
</script>

<style scoped>
  .wrapper{
    backdrop-filter: blur(5px);
    top: 0;
    left: 0;
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100%;
    background-color: rgba(0,0,0,0.7);

  }
  .modal{
    margin: 0px 30px 0px 30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 400px;
    height: 120px;
    background-color: white;
    font-size: 30px;
    align-items: center;
    color: black;
    box-shadow: 0 0 10px rgba(0,0,0,0.5);
     border: 3px solid #3FB0C5;
  }
  .modal-text{
    text-align: center;
  }
  .close{
    background-color: transparent;
    margin-top: 20px;
    padding: 10px;
    width: 100px;
    border: 1px solid black;
    cursor: pointer;
    transition: 0.3s linear;
    font-size: 14px;
   
  }
  .close:hover{
    border: 1px solid #3FB0C5;
    color: #3FB0C5;
  }

  @media screen and (max-width: 400px){
   .modal{
    margin: 0px 30px 0px 30px;
    width: 200px;
    height: 200px;
  }
    
  }
</style>