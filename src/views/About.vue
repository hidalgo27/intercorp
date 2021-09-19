<template>
  <div class="mx-auto container">
    <div class="shadow-lg rounded-2xl bg-white m-auto p-6 text-center">
      <h1 class="text-5xl font-semibold text-blue-800">Nuestros valores</h1>
      <p class="text-lg text-gray-500 my-6">Estan siempre alli para guiarnos y son consistentemente aplicados en todo Intercorp:</p>

      <p class="text-3xl font-normal text-blue-800">Transparencia . Espíritu de superación Trabajo en equipo . Humildad</p>
    </div>
  </div>
  <section class="mt-12">
    <img src="https://i.ytimg.com/vi/kmRUH1S3RbA/maxresdefault.jpg" alt="" class="h-full w-full">
  </section>
</template>
<script>
export default {
  name: "regular-modal",
  data() {
    return {
      showModal: false
    }
  },
  methods: {
    toggleModal: function(){
      this.showModal = !this.showModal;
    }
  }
}
</script>