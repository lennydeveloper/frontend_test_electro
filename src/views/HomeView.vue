<template>
  <div class="bg-white">
    <h1 class="mt-5 -mb-5 tracking-tight font-semibold text-2xl text-black">UNSPLASH PHOTO GALLERY</h1>
    <!-- search form -->
    <SearchFormComponent @search-photos="searchPhotos">
    </SearchFormComponent>
    <!-- end search form -->

    <!-- card -->
    <div class="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
      <div class="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
        <div v-for="item in photos" :key="item.id">
          <ImageCard @show-like-modal="showLikeModal" :image="item" :favorites="false">
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

    <!-- like modal -->
    <ModalComponent v-if="showModal" @like-modal-action="likePhotoAction" @cancel-modal-action="cancelLikeAction">
    </ModalComponent>
    <!-- end like modal -->
  </div>
</template>

<script>
import axios from 'axios';
// Components
import SearchFormComponent from '../components/SearchForm.vue'
import ImageCard from '../components/ImageCard.vue'
import ModalComponent from '../components/ModalComponent.vue'

export default {
  name: 'HomeView',
  data() {
    return {
      photos: [],
      image_id: null,
      showModal: false,
      search: '',
      unselected: 'relative inline-flex items-center border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-500 hover:bg-gray-50 focus:z-20 hover:bg-indigo-50 hover:border-indigo-500 hover:z-20',
      selected: 'relative z-10 inline-flex items-center border border-indigo-500 bg-indigo-50 px-4 py-2 text-sm font-medium text-indigo-600 focus:z-20',
    }
  },
  components: {
    SearchFormComponent,
    ImageCard,
    ModalComponent
  },
  beforeCreate() {
    axios.get('http://127.0.0.1:3000/random-photos?topics=xHxYTMHLgOc,xjPR4hlkBGA')
      .then(response => {
        this.photos = response.data;
      }).catch(err => {
        console.error(err);
        alert('Error al obtener las imágenes random');
      });
  },
  methods: {
    searchPhotos(value) {
      this.search = value;
      axios.get(`http://127.0.0.1:3000/api/search/photos?search=${this.search}&page=1`)
        .then(response => {
          this.photos = response.data.results;
        }).catch(err => {
          console.error(err);
          alert('Error al buscar imágenes con palabra clave');
        });
    },
    showLikeModal(value) {
      this.image_id = value;
      this.showModal = true;
    },
    likePhotoAction() {
      axios.get(`http://127.0.0.1:3000/api/photos/like?id=${this.image_id}`)
        .then(response => {
          if (response.status == 200) {
            alert('La imagen ha sido marcada como favorita');
          }
        }).catch(err => {
          console.error(err);
          alert('Error al marcar la imagen como favorita');
        })
      this.showModal = false;
    },
    cancelLikeAction() {
      this.showModal = false;
    }
  }
}
</script>