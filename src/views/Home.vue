<template>
  <div class="">
    <div class="mx-auto container">
      <div class="shadow-lg w-1/2 rounded-2xl bg-white m-auto p-2">

        <div class="p-4">
          <div class="w-full mx-auto p-1 pr-0 flex items-center gap-4">
            <div class="flex-1 flex inline-flex items-center gap-x-4">
              <span class="font-semibold text-gray-500">JSON Matriz Input:</span>
              <input type="text" v-model="matrix" class="form-input flex-1" />
            </div>
            <div class="w-auto">
              <button
                  type="button"
                  class="btn-primary text-center"
                  @click="rotate()"
              >
                Rotar
              </button>
            </div>
          </div>
          <div
              class="text-red-500 mt-2 mb-3 text-xs text-center"
              v-if="error_v.length > 0"
          >
            <ul>
              <li
                  v-for="er in error_v"
                  :key="er"
              >
                {{er}}
              </li>
            </ul>
          </div>

            <div class="grid mt-6" v-if="result.length > 0" :class="{ 'grid-cols-2': result.length === 2, 'grid-cols-3': result.length === 3}">
              <div class="text-center font-semibold text-gray-500" :class="{ 'col-span-2': result.length === 2, 'col-span-3': result.length === 3}">
                <p>Resultado:</p>
              </div>
              <template v-for="matrix_arr in result">
                <div v-for="matrix_arr_sub in matrix_arr" class="border p-6 text-center">
                  {{ matrix_arr_sub }}
                </div>
              </template>
            </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import { reactive, ref, toRefs } from "vue";
export default {
  // Usamos la función setup(vue3) en vez de data(vue2)
  setup() {

    // Usamos ref por que nos permite crear información reactiva
    // ref hace referencia  a la clase RefImpl estas instancia tiene internamente un value -> puede ser String, Number, Array, Object
    const matrix = ref([]);
    const result = ref( []);

    // Usamos reactive para crear información reactiva. Nos permite crear información como si fuese un objeto de data.
    // La propiedad reactiva al igual que data corresponde a un tipo de propiedad reactiva.
    const State = reactive({
      error_v: [],
    });

    // Creamos una funcion como si fuese un method en vue2
    // Usamos .value por que vue observa los values de alguna referencia
    function rotate() {
      State.error_v = []; // Elimino los errore anteriores
      if (matrix.value.length === 0) {
        State.error_v.push("Ingrese el arreglo"); // envīo error
      }

      //utilizo transpose, reduce, map y finalmente reverse.
      const transpose = array => array.reduce((r, a) => a.map((v, i) => [...(r[i] || []), v]), []),
          matriz = transpose(JSON.parse(matrix.value)).reverse();
      // agrego el result a la variable 'result'
      result.value = matriz;
    }

    //Las funciones setup siempre tienen que retornar un objeto
    return {
      ...toRefs(State),
      matrix,
      result,

      rotate,
    };
  },
};
</script>
