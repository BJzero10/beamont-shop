<template>
  <div
    class="bg-indigo-600 rounded-xl h-64 flex flex-col items-center justify-center"
  >
    <h2 class="text-3xl font-bold text-white my-4">Boletín informativo</h2>
    <p class="mb-4 text-white text-lg">
      ¡Suscríbete para recibir descuentos y más!
    </p>
    <input
      type="email"
      placeholder="Déjanos tu correo"
      class="input input-bordered input-primary w-full max-w-xs bg-indigo-600 border-[1px] border-white mb-3"
      v-model="email"
    />
    <button
      v-if="isEmail(email)"
      @click="submit"
      class="btn bg-white text-indigo-600 border-none w-[20rem] hover:bg-white/80"
    >
      Suscríbete
    </button>
    <button
      v-else
      @click="emailError"
      class="btn bg-white text-indigo-600 border-none w-[20rem] hover:bg-white/80"
    >
      Suscríbete
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: null,
    };
  },
  methods: {
    async submit() {
      await this.$swal({
        title: "Muchas gracias por suscribirte",
        icon: "success",
        allowOutsideClick: false,
        allowEscapeKey: false,
        timer: 4000,
        timeProgressBar: true,
        showConfirmButton: false,
        text: "Se le notificará cuando tengamos una oferta o artículos a la venta.",
      });
      console.log(this.email);
    },
    isEmail(email) {
      let emailRegex =
        /^(([^<>()[\]\.,;:\s@\"]+(\.[^<>()[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i;
      if (emailRegex.test(email)) {
        return true;
      } else {
        return false;
      }
    },
    emailError() {
      alert("Por favor ingrese una dirección de correo válido");
      return true;
    },
  },
};
</script>

<style></style>
