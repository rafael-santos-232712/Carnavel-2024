<script setup>
import { onMounted, ref, computed } from 'vue';
import SambaSchoolCard from '../components/SambaSchoolCard.vue'
import SambaSchoolForm from '../components/SambaSchoolForm.vue'

const formModal = ref(null)
const sambaSchools = ref([])

const getSambaSchools = async function() {
  // TODO: Criar código para pegar dados do backend

  sambaSchools.value = [
    {
      id: 1,
      name: 'Gaviões',
      imageUrl: 'https://sismf.museudofutebol.org.br/anexos/imagem/525017/w:640/h:640/c:0',
      age: 300,
      presentationDate: '2023-02-12',
      avaliation: 10
    },
    {
      id: 2,
      name: 'Beija-flor',
      imageUrl: 'https://picsum.photos/200/300',
      age: 301,
      presentationDate: '2023-02-12',
      avaliation: 9.7
    },
    {
      id: 3,
      name: 'Vila Izabel',
      imageUrl: 'https://sismf.museudofutebol.org.br/anexos/imagem/525017/w:640/h:640/c:0',
      age: 300,
      presentationDate: '2023-02-12',
      avaliation: 9.5
    },
  ]
}

const formSambaSchool = ref({})
const editSambaSchool = (sambaSchool) => {
  formSambaSchool.value = sambaSchool;
  formModal.value.show()
}
const newSambaSchool = () => {
  console.log("newSambaSchool")
  formSambaSchool.value = {};
  formModal.value.show()
}
const deleteSambaSchool = async (sambaSchool) => {
  console.log("deleteSambaSchool: ", sambaSchool)

  sambaSchools.value = sambaSchools.value.filter(item => item.id != sambaSchool.id)

  // TODO: Criar código para apagar dado no backend
}
const saveSambaSchool = () => {
  console.log("saveSambaSchool: ", formSambaSchool.value)

  if (formSambaSchool.value.id) return;

  sambaSchools.value = [...sambaSchools.value, formSambaSchool.value]
  formModal.value.hide()

  // TODO: Criar código para salvar dado no backend
}

onMounted(() => {
  getSambaSchools()
})
</script>

<template>
  <main>
    <b-button variant="primary" @click="newSambaSchool()">Criar</b-button>

    <b-container fluid>
      <b-row class="my-1">
        <b-col v-for="sambaSchool in sambaSchools" sm="6" md="4">
          <samba-school-card
            :samba-school="sambaSchool"
            @edit="editSambaSchool(sambaSchool)"
            @delete="deleteSambaSchool(sambaSchool)"
          ></samba-school-card>
        </b-col>
      </b-row>
    </b-container>  

    <b-modal ref="formModal" hide-footer title="Formulário de Escola de Samba">
      <div class="d-block text-center">
        <samba-school-form :samba-school="formSambaSchool" />
      </div>
      <b-button class="mt-3" variant="outline-danger" block>Fechar</b-button>
      <b-button @click="saveSambaSchool()" class="mx-2 mt-3" variant="outline-success">Salvar</b-button>
    </b-modal>
  </main>
</template>
