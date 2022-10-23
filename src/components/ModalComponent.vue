<template>
    <!-- Like modal -->
    <div class="relative z-10" aria-labelledby="modal-title" role="dialog" aria-modal="true">
        <!--
              Background backdrop, show/hide based on modal state.

              Entering: "ease-out duration-300"
              From: "opacity-0"
              To: "opacity-100"
              Leaving: "ease-in duration-200"
              From: "opacity-100"
              To: "opacity-0"
          -->
        <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>

        <div class="fixed inset-0 z-10 overflow-y-auto">
            <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
                <!--
                      Modal panel, show/hide based on modal state.

                      Entering: "ease-out duration-300"
                      From: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                      To: "opacity-100 translate-y-0 sm:scale-100"
                      Leaving: "ease-in duration-200"
                      From: "opacity-100 translate-y-0 sm:scale-100"
                      To: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                  -->
                <div
                    class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg">
                    <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
                        <div class="sm:flex sm:items-start">
                            <div
                                class="mx-auto flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full bg-blue-100 sm:mx-0 sm:h-10 sm:w-10">

                                <!-- Heroicon name: outline/exclamation-triangle -->
                                <svg class="h-6 w-6 text-blue-600" xmlns="http://www.w3.org/2000/svg" fill="none"
                                    viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M6.633 10.5c.806 0 1.533-.446 2.031-1.08a9.041 9.041 0 012.861-2.4c.723-.384 1.35-.956 1.653-1.715a4.498 4.498 0 00.322-1.672V3a.75.75 0 01.75-.75A2.25 2.25 0 0116.5 4.5c0 1.152-.26 2.243-.723 3.218-.266.558.107 1.282.725 1.282h3.126c1.026 0 1.945.694 2.054 1.715.045.422.068.85.068 1.285a11.95 11.95 0 01-2.649 7.521c-.388.482-.987.729-1.605.729H13.48c-.483 0-.964-.078-1.423-.23l-3.114-1.04a4.501 4.501 0 00-1.423-.23H5.904M14.25 9h2.25M5.904 18.75c.083.205.173.405.27.602.197.4-.078.898-.523.898h-.908c-.889 0-1.713-.518-1.972-1.368a12 12 0 01-.521-3.507c0-1.553.295-3.036.831-4.398C3.387 10.203 4.167 9.75 5 9.75h1.053c.472 0 .745.556.5.96a8.958 8.958 0 00-1.302 4.665c0 1.194.232 2.333.654 3.375z" />
                                </svg>
                            </div>
                            <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
                                <h3 class="text-lg font-medium leading-6 text-gray-900" id="modal-title">Like the
                                    image</h3>
                                <div class="mt-2">
                                    <p class="text-sm text-gray-500">Are you sure you want to like the image?</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="bg-gray-50 px-4 py-3 sm:flex sm:flex-row-reverse sm:px-6">
                        <button @click="likeModalButton" type="button"
                            class="inline-flex w-full justify-center rounded-md border border-transparent bg-blue-500 px-4 py-2 text-base font-medium text-white shadow-sm hover:bg-blue-600 focus:outline-none sm:ml-3 sm:w-auto sm:text-sm">Like</button>
                        <button @click="cancelModalLikeButton" type="button"
                            class="mt-3 inline-flex w-full justify-center rounded-md border border-gray-300 bg-white px-4 py-2 text-base font-medium text-gray-700 shadow-sm hover:bg-gray-50 focus:outline-none sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm hover:bg-gray-100">Cancel</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- end like modal-->
</template>

<script>
export default {
    data() {
        return {
            showModal: false
        }
    },
    name: 'ModalComponent',
    methods: {
        likeModalButton() {
            this.$emit('like-modal-action', null);
        },
        cancelModalLikeButton() {
            this.$emit('cancel-modal-action', null);
        }
    }
}
</script>

<style>

</style>