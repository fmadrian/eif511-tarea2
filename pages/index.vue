<template>
    <div class="container">
        <div class="d-flex flex-column row-gap-4">
            <HeaderView />

            <div class="d-flex flex-column row-gap-2">
                <h1>Proyecto 1</h1>
                <h3>Arquitectura de información</h3>
                <div class="d-flex flex-column">
                    <h5>Fernanda Quesada</h5>
                    <h5>Adrián Fallas</h5>
                </div>
            </div>

            <div class="row">
                <NuxtLink class="px-5 py-2 col-4 text-decoration-none" v-for="(item, index) in menu" :key=index
                    :href=item.url>
                    <div class="card">
                        <img class="card-img-top" :height=250 :alt=item.nombre :src=item.image />
                        <div class="card-body">
                            <h5 class="card-title">{{ item.nombre }}</h5>
                        </div>
                    </div>
                </NuxtLink>
            </div>
            <FooterView />
        </div>
    </div>
</template>
<script setup>

const menu = ref([
    { nombre: "Películas", image: "https://cdn.pixabay.com/photo/2019/05/19/10/40/cinema-4213751_1280.jpg", url: "/pelicula" },
    { nombre: "Directores", image: "https://cdn.pixabay.com/photo/2024/05/10/18/54/silhouette-8753498_1280.jpg", url: "/director" },
    { nombre: "Estudios", image: "https://cdn.pixabay.com/photo/2020/06/21/11/38/universal-studio-5324469_1280.jpg", url: "/estudio" },
])
</script>
