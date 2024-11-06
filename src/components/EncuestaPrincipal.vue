<template>
  <div>
    <h1>{{ datosEncuesta.title }}</h1>
    <div v-for="(question, index) in datosEncuesta.questions" :key="index">
      <p>{{ question.title }}</p>
      <div v-if="question.type === 'MULTIPLE_CHOICE'">
        <!-- Agrupamos los botones por pregunta usando un nombre único -->
        <div v-for="(option, idx) in question.options" :key="idx" class="opcion">
          <label>
            <input
              type="radio"
              :name="getQuestionName(question)"
              :value="option"
              v-model="respuestaSeleccionada[question._id.$oid]" 
            />
            {{ option }}
          </label>
        </div>
      </div>
      <div v-if="question.type === 'TEXT'">
        <textarea placeholder="Escribe tu respuesta aquí..." v-model="respuestaSeleccionada[question._id.$oid]"></textarea>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    datosEncuesta: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      // Usamos un objeto para almacenar las respuestas de cada pregunta
      respuestaSeleccionada: {}
    };
  },
  methods: {
    // Genera un nombre único para cada grupo de radio buttons, basado en el ID de la pregunta
    getQuestionName(question) {
      return question._id.$oid;  // Devolvemos el ID de la pregunta como nombre único
    }
  }
};
</script>

<style scoped>
.opcion {
  margin-bottom: 10px;
}
</style>
