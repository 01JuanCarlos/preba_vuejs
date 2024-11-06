<template>
  <div class="pregunta">
    <h3>{{ pregunta.title }}</h3>
    <textarea
      v-model="respuestaTexto"
      placeholder="Escribe tu respuesta..."
    ></textarea>
  </div>
</template>

<script>
export default {
  props: {
    pregunta: {
      type: Object,
      required: true
    },
    modelValue: {
      type: String,
      default: ""
    }
  },
  emits: ['update:modelValue'],
  computed: {
    respuestaTexto: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit('update:modelValue', value);
      }
    }
  }
};
</script>
