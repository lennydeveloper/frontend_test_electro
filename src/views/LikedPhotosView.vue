<template>
    <div class="bg-white">
        <h1 class="mt-5 -mb-5 tracking-tight font-semibold text-2xl text-black">UNSPLASH PHOTO GALLERY</h1>
        <!-- card -->
        <div class="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
            <div class="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
                <div v-for="item in photos" :key="item.id">
                    <ImageCard :image="item" :favorites="true">
                    </ImageCard>
                </div>
            </div>
        </div>
        <!-- end card -->

        <!-- pagination buttons -->
        <!-- <div class="flex flex-1 justify-end px-16 mt-20 -mb-16 items-start">
            <a style="cursor: pointer" @click="actualPage > 1 ? actualPage = actualPage - 1 : actualPage = 1"
                class="relative inline-flex items-center rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 hover:bg-gray-50">Previous</a>
            <a style="cursor: pointer"
                @click="actualPage < pageLimit ? actualPage = actualPage + 1 : actualPage = pageLimit"
                class="relative ml-3 inline-flex items-center rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 hover:bg-gray-50">Next</a>
        </div> -->
        <!-- end pagination -->
    </div>
</template>
  
<script>
import axios from 'axios'
import ImageCard from '../components/ImageCard.vue'
export default {
    name: 'LikedPhotosView',
    data() {
        return {
            photos: []
        }
    },
    components: {
        ImageCard
    },
    beforeCreate() {
        axios.get('http://127.0.0.1:3000/api/user/likes')
            .then(response => {
                this.photos = response.data;
            }).catch(err => {
                console.error(err);
                alert('Error al obtener las imágenes favoritas');
            });
    },
}
</script>
  
<style>

</style>