<!-- pages/authors_index.vue -->
<template>
    <div class="container">
        <HeaderView />
        <div class="row mt-4">
            <h1>Directores</h1>
            <p>En esta sección podrá observar la lista de directores involucrados con las peliculas animadas.</p>
        </div>
        <div class="row gx-5 gy-5">
            <NuxtLink class="col-3 text-decoration-none" :to="`/director/${director.id}`" v-for="director in directores"
                :key="director.id">
                <div class="card">
                    <img class="card-img-top" width="200" height="200" :src="director.image" />
                    <div class="card-body">
                        <h5 class="card-title">{{ director.nombre }}</h5>
                    </div>
                </div>
            </NuxtLink>
        </div>
        <FooterView />
    </div>
</template>
<script setup>
const directores = (await queryContent('/director').only('body').findOne()).body;
</script>