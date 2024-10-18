<!-- pages/peliculas_index.vue -->
<template>
    <div class="container">
        <HeaderView />
        <h3 style="margin-top: 15px">Peliculas Animadas</h3>
        <p>En está sección podrá observar la lista de peliculas animadas</p>
            <div class="row">
                <div class="col-md-4 mb-4" v-for="pelicula in peliculas" :key="pelicula.id">
                    <NuxtLink :to="`pelicula/${pelicula.id}`" class="card-link  text-decoration-none">
                        <div class="card" style="width: 18rem;">
                            <img :src="pelicula.img" class="card-img-top" alt="Pelicula" style="height: 300px; object-fit: cover;">
                            <div class="card-body">
                            <h5 class="card-title">{{ pelicula.title }}</h5>
                            <p class="card-text">{{ pelicula.description }}</p>
                            </div>
                        </div>
                    </NuxtLink>

                </div>
            </div>       
        <FooterView />
    </div>
</template>

<script setup>
const data = await queryContent('/pelicula').only('body').findOne() 
const peliculas = data.body;
</script>