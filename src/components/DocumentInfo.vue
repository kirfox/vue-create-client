<template>
  <div class="document-info">
    <div class = "personal-info__column1">
      <label for="document">Тип документа<span class='required'>*</span></label>
      <select size="1" id="document">
        <option>Паспорт</option>
        <option>Свидетельство о рождении</option>
        <option>Вод. удостоверение</option>
      </select>

      <InputItem 
        v-bind:label="'Кем выдан'"
        v-bind:placeholder="'ГУ МВД по г.Москве'"
        v-bind:id="'organization'"
        v-bind:required="false"
        v-bind:rules="organization"
      />
    </div>
    <div class = "personal-info__column2">
       <InputItem 
        v-bind:label="'Номер'"
        v-bind:placeholder="'1234'"
        v-bind:id="'number'"
        v-bind:required="false"
        v-bind:rules="number"
      />
      <InputItem 
        v-bind:label="'Серия'"
        v-bind:placeholder="'12345678'"
        v-bind:id="'seria'"
        v-bind:required="false"
        v-bind:rules="seria"
      />
    </div>
    <div class = "personal-info__column3">
      <InputItem 
        v-bind:label="'Дата выдачи'"
        v-bind:placeholder="'12.01.2018'"
        v-bind:id="'dateOfIssue'"
        v-bind:required="true"
        v-bind:rules="dateOfIssue"
      />
    </div>
  </div>
</template>

<script>
import InputItem from './InputItem';
  export default {
    name: 'DocumentInfo',
    components: {
      InputItem
    },
    data: () => ({
      organization:[
        {
          regExp: /^[а-яА-Яa-z A-Z]+$/,
          errorText: 'В данном поле запрещенны цифры'
        }
      ],
      number:[
        {
          regExp: /^\d{4,4}$/,
          errorText: 'Введите корректный номер'
        }
      ],
      seria:[
        {
          regExp: /^\d{8,8}$/,
          errorText: 'Введите корректную серию'
        }
      ],
      dateOfIssue:[
        {
          regExp: /^(?:(?:31(\/|-|\.)(?:0?[13578]|1[02]))\1|(?:(?:29|30)(\/|-|\.)(?:0?[1,3-9]|1[0-2])\2))(?:(?:1[6-9]|[2-9]\d)?\d{2})$|^(?:29(\/|-|\.)0?2\3(?:(?:(?:1[6-9]|[2-9]\d)?(?:0[48]|[2468][048]|[13579][26])|(?:(?:16|[2468][048]|[3579][26])00))))$|^(?:0?[1-9]|1\d|2[0-8])(\/|-|\.)(?:(?:0?[1-9])|(?:1[0-2]))\4(?:(?:1[6-9]|[2-9]\d)?\d{2})$/,
          errorText: 'Введите корректную дату'
        }
      ]
    })
  }
</script>

