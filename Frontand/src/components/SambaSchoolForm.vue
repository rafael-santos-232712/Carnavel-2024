<script setup>
import { computed } from 'vue';

const props = defineProps({
    sambaSchool: Object,
})
</script>

<template>
  <b-container fluid>
    <b-row class="my-1">
      <b-col sm="3">
        <label :for="`type-text`">Nome:</label>
      </b-col>
      <b-col sm="9">
        <b-form-input v-model="sambaSchool.name" :id="`type-text`" type="text"></b-form-input>
      </b-col>
    </b-row>
    <b-row class="my-1">
      <b-col sm="3">
        <label :for="`type-text`">URL Imagem:</label>
      </b-col>
      <b-col sm="9">
        <b-form-input v-model="sambaSchool.imageUrl" :id="`type-text`" type="text"></b-form-input>
      </b-col>
    </b-row>
    <b-row class="my-1">
      <b-col sm="3">
        <label :for="`type-number`">Idade:</label>
      </b-col>
      <b-col sm="9">
        <b-form-input v-model="sambaSchool.age" :id="`type-number`" type="number"></b-form-input>
      </b-col>
    </b-row>
    <b-row class="my-1">
      <b-col sm="3">
        <label :for="`type-date`">Data da Apresentação:</label>
      </b-col>
      <b-col sm="9">
        <b-form-input v-model="sambaSchool.presentationDate" :id="`type-date`" type="date"></b-form-input>
      </b-col>
    </b-row>
  </b-container>
</template>


<style>
.teste {
    color: rgb(255, 0, 0)
}
</style>
