<!-- pages/books/[...slug].vue -->
<template>
    <div class="container">
        <HeaderView />
        <div class="row py-4 gx-4">
            <div class="col-4 text-center">
                <img class="img-fluid" :src=estudio.image :alt=estudio.nombre />
            </div>
            <div class="col-8 container">
                <div class="row mb-4">
                    <h1><strong>{{ estudio.nombre }}</strong></h1>
                </div>
                <hr />
                <div class="row mb-4">
                    <div class="col-6">
                        <span class="fs-4"><strong>Ubicación:</strong> {{ estudio.ubicacion }}</span>
                    </div>
                    <div class="col-6">
                        <span class="fs-4"><strong>Año de fundación:</strong> {{ estudio.fundacion }}</span>
                    </div>
                </div>
                <hr />
                <div class="row mb-2">
                    <h3>Peliculas: </h3>
                </div>
                <div class="row">
                    <MovieCard v-for="(pelicula, index) in peliculas" :key=index :pelicula=pelicula />
                </div>
            </div>
        </div>
        <FooterView />
    </div>
</template>
<script setup>
import MovieCard from '~/components/MovieCard.vue';

const route = useRoute()
const estudio = (await queryContent('/estudio').only('body').findOne())
    .body.find(estudio => estudio.id == route.params.id)

const peliculas = (await queryContent('pelicula').only('body').findOne())
    .body
    .filter(p => estudio.peliculas.includes(p.id));

</script>