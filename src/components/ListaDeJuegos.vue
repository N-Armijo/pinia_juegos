<script setup>
import { useJuegosStore } from '@/stores/piniaStore'
import { storeToRefs } from 'pinia'

const juegosStore = useJuegosStore()
const { juegos } = storeToRefs(juegosStore)
const { incrementar, decrementar } = juegosStore // va desestructurando

</script>
<template>
    <div class="row">
        <h1 class="m-5 text-center">Lista de juegos</h1>
        <div class="col-6 mx-auto">
            <table class="table table-striped">
                <thead>
                    <tr>
                        <th>Nombre Juego</th>
                        <th>Stock</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="juego, i in juegos" :key="juego.id">
                        <td>{{ juego.nombre }}</td>
                        <td>{{ juego.stock }}</td>
                        <td>
                            <button @click="decrementar(i)" class="btn btn-danger me-1">-</button>
                            <!--No olvidar pasar el parametro del index a la funcion-->
                            <button @click="incrementar(i)" class="btn btn-success">+</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

</template>