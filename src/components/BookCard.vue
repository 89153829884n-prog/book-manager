<template>
<div class="col-md-6 mb-3">
<div class="card h-100" :class="{'bg-light':book.completed}">
<div class="card-body">
<h5 class="card-title">{{book.title}}</h5>
<h6 class="card-subtitle mb-2 text-muted">{{book.author}}</h6>
<span class="badge bg-secondary mb-2">{{book.genre}}</span>
<div class="d-flex align-items-center gap-2 flex-wrap">
<div v-if="book.completed" class="rating me-2">
<span v-for="star in 5" :key="star" @click="$emit('rate',star)" class="fs-5" :class="{'text-warning':star<=book.rating,'text-secondary':star>book.rating}" style="cursor:pointer;">
{{star<=book.rating?'★':'☆'}}
</span>
</div>
<button @click="$emit('toggle')" :class="['btn btn-sm',book.completed?'btn-outline-success':'btn-success']">
{{book.completed?'Прочитано':'Отметить'}}
</button>
<button @click="$emit('delete')" class="btn btn-sm btn-outline-danger">Удалить</button>
</div>
</div>
</div>
</div>
</template>
<script setup>
defineProps(['book'])
defineEmits(['toggle','delete','rate'])
</script>