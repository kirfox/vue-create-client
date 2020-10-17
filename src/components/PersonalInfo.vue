<template>
  <div class='personal-info'>
      <div class="personal-info__column1">
        <InputItem 
          v-bind:label="'Фамилия'"
          v-bind:placeholder="'Иванов'"
          v-bind:id="'surname'"
          v-bind:required="true"
          v-bind:rules="surNameErrors"
        />

        <InputItem 
          v-bind:label="'Имя'"
          v-bind:placeholder="'Иван'"
          v-bind:id="'firstName'"
          v-bind:required="true"
          v-bind:rules="nameErrors"
      
        />

        <InputItem 
          v-bind:label="'Отчество'"
          v-bind:placeholder="'Иванович'"
          v-bind:id="'secondName'"
          v-bind:required="true"
          v-bind:rules="secondNameErrors"
        />
      </div>
      <div class="personal-info__column2">
        <InputItem 
          
          v-bind:label="'Дата рождения'"
          v-bind:placeholder="'дд.мм.гггг'"
          v-bind:id="'birthday'"
          v-bind:required="true"
          v-bind:rules="birthday"
          
        />

        <InputItem 
          v-bind:label="'Телефон'"
          v-bind:placeholder="'79191234567'"
          v-bind:id="'phone'"
          v-bind:required="true"
          v-bind:rules="phone"
         
        />

        <label for="sex">Пол</label>
        <select id="sex">
          <option>Мужской</option>
          <option>Женский</option>
        </select>
      </div>
      <div class="personal-info__column3">
        <label for="doctor">Лечащий врач</label>
        <select size="1" id="doctor">
          <option>Иванов</option>
          <option>Захаров</option>
          <option>Чернышева</option>
        </select>
        <label for="clients">Группа клиентов<span class='required'>*</span></label>
        <select multiple size="3" ref="clients" id="clients">
          <option>VIP</option>
          <option>Проблемные</option>
          <option>ОМС</option>
        </select>
        <span class="clients-error"></span>
        <div class="container-checkbox">
          <label for="SMS">Отправка СМС:</label>
          <p> <input type="checkbox" id="SMS"> Не отправлять СМС</p>
        </div>
      </div>
    </div>
</template>

<script>
import InputItem from './InputItem';
  export default {
    name: 'PersonalInfo',
    components: {
      InputItem
    },
    data: () => ({
      surNameErrors:[
        {
          regExp: /^([А-Я]{1}[а-яё]{1,23}|[A-Z]{1}[a-z]{1,23})$/,
          errorText: 'Введите корректную фамилию'
        }
      ],
      nameErrors:[
        {
          regExp: /^([А-Я]{1}[а-яё]{1,23}|[A-Z]{1}[a-z]{1,23})$/,
          errorText: 'Введите корректное имя'
        }
      ],
      secondNameErrors:[
        {
          regExp: /^([А-Я]{1}[а-яё]{1,23}|[A-Z]{1}[a-z]{1,23})$/,
          errorText: 'Введите корректное Отчество'
        }
      ],
      birthday:[
        {
          regExp: /^(?:(?:31(\/|-|\.)(?:0?[13578]|1[02]))\1|(?:(?:29|30)(\/|-|\.)(?:0?[1,3-9]|1[0-2])\2))(?:(?:1[6-9]|[2-9]\d)?\d{2})$|^(?:29(\/|-|\.)0?2\3(?:(?:(?:1[6-9]|[2-9]\d)?(?:0[48]|[2468][048]|[13579][26])|(?:(?:16|[2468][048]|[3579][26])00))))$|^(?:0?[1-9]|1\d|2[0-8])(\/|-|\.)(?:(?:0?[1-9])|(?:1[0-2]))\4(?:(?:1[6-9]|[2-9]\d)?\d{2})$/,
          errorText: 'Введите корректную дату'
        }
      ],
      phone:[
        {
          regExp: /^7\d{10}$/,
          errorText: 'Введите корректный телефон пример: 79191234567'
        }
      ]
    }),
  }
</script>

<style>
  .clients-error{
    display: none;
    color: red;
  }
</style>