<template>
  <div class="pregunta">
    <h3>{{ pregunta.title }}</h3>
    <div v-for="opcion in pregunta.options" :key="opcion" class="opcion">
      <label>
        <input
          type="radio"
          :name="pregunta._id.$oid"
          :value="opcion"
          v-model="respuestaSeleccionada"
        />
        {{ opcion }}
      </label>
    </div>
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
    respuestaSeleccionada: {
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

<style scoped>
.opcion {
  display: inline-block;
  margin-right: 10px;
}
</style>
