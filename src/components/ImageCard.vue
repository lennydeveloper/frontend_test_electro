<template>
    <div>
        <!-- card -->
        <a class="group">
            <div
                class="aspect-w-1 aspect-h-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-w-7 xl:aspect-h-8">
                <img :src="image.urls.small_s3" :alt="image.alt_description == null ? '' : image.alt_description"
                    class="h-full w-full object-cover object-center group-hover:opacity-75">
            </div>
            <div class="flex items-end content-around">
                <div class="flex-1 flex-col content-start">
                    <p class="text-left text-gray-600 text-sm mt-2">@{{ image.user.username }}</p>
                    <div class="flex items-center mt-2">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                            stroke="currentColor" class="w-6 h-6">
                            <path stroke-linecap="round" stroke-linejoin="round"
                                d="M21 8.25c0-2.485-2.099-4.5-4.688-4.5-1.935 0-3.597 1.126-4.312 2.733-.715-1.607-2.377-2.733-4.313-2.733C5.1 3.75 3 5.765 3 8.25c0 7.22 9 12 9 12s9-4.78 9-12z" />
                        </svg>
                        <span class="font-semibold tracking-tighter text-xl p-0 m-0 ml-1 text-gray-600">{{
                        image.likes }}</span>
                    </div>
                </div>
                <div v-if="!favorites">
                    <button @click="showLikeModal(image.id)"
                        class="btn inline-block px-4 py-2 bg-blue-600 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700  focus:shadow-lg focus:outline-none focus:ring-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out flex items-center"
                        type="submit" id="button-addon2">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                            stroke="currentColor" class="w-6 h-6">
                            <path stroke-linecap="round" stroke-linejoin="round"
                                d="M6.633 10.5c.806 0 1.533-.446 2.031-1.08a9.041 9.041 0 012.861-2.4c.723-.384 1.35-.956 1.653-1.715a4.498 4.498 0 00.322-1.672V3a.75.75 0 01.75-.75A2.25 2.25 0 0116.5 4.5c0 1.152-.26 2.243-.723 3.218-.266.558.107 1.282.725 1.282h3.126c1.026 0 1.945.694 2.054 1.715.045.422.068.85.068 1.285a11.95 11.95 0 01-2.649 7.521c-.388.482-.987.729-1.605.729H13.48c-.483 0-.964-.078-1.423-.23l-3.114-1.04a4.501 4.501 0 00-1.423-.23H5.904M14.25 9h2.25M5.904 18.75c.083.205.173.405.27.602.197.4-.078.898-.523.898h-.908c-.889 0-1.713-.518-1.972-1.368a12 12 0 01-.521-3.507c0-1.553.295-3.036.831-4.398C3.387 10.203 4.167 9.75 5 9.75h1.053c.472 0 .745.556.5.96a8.958 8.958 0 00-1.302 4.665c0 1.194.232 2.333.654 3.375z" />
                        </svg>
                    </button>
                </div>
            </div>
        </a>
        <!-- end card -->
    </div>
</template>

<script>
export default {
    props: ['image', 'favorites'],
    name: 'ImageCard',
    data() {
        return {
            // favorites: this.$props.favorites
        }
    },
    methods: {
        showLikeModal(id) {
            this.$emit('show-like-modal', id);
        }
    },
    created() {
        console.log(this.favorites);
    }
}
</script>

<style>

</style>