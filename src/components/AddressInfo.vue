<template>
  <div class="address-info">
    <div class = "personal-info__column1">
      <InputItem 
        v-bind:label="'Индекс'"
        v-bind:placeholder="'117393'"
        v-bind:id="'index'"
        v-bind:required="false"
        v-bind:rules="index"
      />

      <InputItem 
        v-bind:label="'Страна'"
        v-bind:placeholder="'Россия'"
        v-bind:id="'country'"
        v-bind:required="false"
        v-bind:rules="country"
      />
    </div>
    <div class = "personal-info__column2"> 
      <InputItem 
        v-bind:label="'Область'"
        v-bind:placeholder="'Московская область'"
        v-bind:id="'area'"
        v-bind:required="false"
        v-bind:rules="area"
      /> 

      <InputItem 
        v-bind:label="'Город'"
        v-bind:placeholder="'Москва'"
        v-bind:id="'city'"
        v-bind:required="true"
        v-bind:rules="city"
      /> 
    </div>  
    <div class = "personal-info__column3"> 
      <InputItem 
        v-bind:label="'Улица'"
        v-bind:placeholder="'Гарибальди'"
        v-bind:id="'street'"
        v-bind:required="false"
      /> 

      <InputItem 
        v-bind:label="'Номер дома'"
        v-bind:placeholder="'11'"
        v-bind:id="'house'"
        v-bind:required="false"
      /> 
    </div>   
  </div>
</template>

<script>
import InputItem from './InputItem';
  export default {
    name: 'AddressInfo',
    components: {
      InputItem
    },
    data: () =>({
      index:[
        {
          regExp: /^\d{6,6}$/,
          errorText: 'Введите корректный индекс'
        }
      ],
      country:[
        {
          regExp: /^[а-яА-Яa-z A-Z]+$/,
          errorText: 'В данном поле запрещенны цифры'
        }
      ],
      area:[
        {
          regExp: /^[а-яА-Яa-z A-Z]+$/,
          errorText: 'В данном поле запрещенны цифры'
        }
      ],
      city:[
        {
          regExp: /^[а-яА-Яa-z A-Z]+$/,
          errorText: 'В данном поле запрещенны цифры'
        }
      ],
    })
  }
  
</script>

