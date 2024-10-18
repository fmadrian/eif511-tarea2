<!-- pages/authors/[...id].vue -->
<template>
    <div class="container">
        <HeaderView />
        <div class="row py-4 gx-4">
            <div class="col-4 text-center">
                <img class="img-fluid" :src=director.image :alt=director.nombre />
            </div>
            <div class="col-8 container">
                <div class="row mb-4">
                    <h1><strong>{{ director.nombre }}</strong></h1>
                </div>
                <hr />
                <div class="row mb-4">
                    <div class="col-6">
                        <span class="fs-4"><strong>Nacionalidad:</strong> {{ director.origen }}</span>
                    </div>
                    <div class="col-6">
                        <span class="fs-4"><strong>Año de nacimiento:</strong> {{ director.nacimiento }}</span>
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
const route = useRoute()

const director = (await queryContent('/director').only('body').findOne()).body
    .find(director => director.id == route.params.id)

const peliculas = (await queryContent('pelicula').only('body').findOne())
    .body
    .filter(p => director.peliculas.includes(p.id));


</script>