<script setup>
import { computed, defineEmits } from 'vue'

const props = defineProps({
    sambaSchool: Object,
})

const emit = defineEmits(['edit', 'delete'])

const formatedDate = computed(() => props.sambaSchool.presentationDate ? new Date(props.sambaSchool.presentationDate).toLocaleString("pt-BR") : "")
</script>

<template>
    <b-card :title="sambaSchool.name" :img-src="sambaSchool.imageUrl" img-alt="Image" img-top tag="article"
        style="max-width: 20rem;" class="mb-2">
        <b-card-text>
            <p>Nota: {{ sambaSchool.avaliation }}</p>
            <p>Idade: {{ sambaSchool.age }}</p>
            <p>Data da apresentação: {{ formatedDate }}</p>
        </b-card-text>

        <b-button variant="primary" @click="emit('edit')">Editar</b-button>
        <b-button variant="primary" @click="emit('delete')">Excluir</b-button>
    </b-card>
</template>

<style>
</style>
