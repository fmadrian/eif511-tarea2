<!-- pages/peliculas/[...id].vue -->
<template>
    <div class="container">
        <HeaderView />
        <div class="row my-5">

            <div class="col-6">
                <img :src="`${pelicula.img}`" style="max-width: 100%;" /> 
            </div>
            <div class="col-6">
                <h3>{{ pelicula.title }}</h3>
                <div class="row mt-3">
                    <div class="col-6">
                        <p><strong>Año de lanzamiento: </strong> {{ pelicula.lanzamiento }}</p> 
                    </div>
                    <div class="col-6">
                        <p><strong>Duración: </strong> {{ pelicula.duracion }}</p> 
                    </div>
                </div>
                <h6><strong>Sinopsis</strong></h6>
                <p style="text-align: justify;">{{ pelicula.sinopsis }}</p>
                <p><strong>Director: </strong><router-link :to="`/director/${pelicula.director}`">{{ directorPelicula.nombre }}</router-link></p>
                <p><strong>Estudio: </strong><router-link :to="`/estudio/${pelicula.estudio}`">{{ estudioPelicula.nombre }}</router-link></p>             
            </div>
        </div>
        <FooterView />
    </div>
</template>
<script setup>
const route = useRoute()

const peliculas  = await queryContent('/pelicula').only('body').findOne()
const pelicula = peliculas.body.find(pelicula => pelicula.id == route.params.id)

const estudios = await queryContent('/estudio').only('body').findOne();
const estudioPelicula = estudios.body.find(estudioPelicula => estudioPelicula.id === pelicula.estudio);

const directores = await queryContent('/director').only('body').findOne();
const directorPelicula = directores.body.find(directorPelicula => directorPelicula.id === pelicula.director);
</script>