<template>
    <NuxtLink class="col-4 py-3 text-decoration-none" :to="`/pelicula/${pelicula.id}`">
        <div class="card">
            <img fit="fill" class="card-img-top" width="200" height="200" :src="pelicula.img" />
            <div class="card-body">
                <h5 class="card-title">{{ pelicula.title }}</h5>
                <p class="card-text">{{ pelicula.description }}</p>
            </div>
        </div>
    </NuxtLink>
</template>

<script setup>

const props = defineProps({
    pelicula: {
        type: Object, required: true
    }
});
</script>