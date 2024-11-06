<template>
  <div>
    <OpcionMultiple 
      v-if="pregunta.type === 'MULTIPLE_CHOICE'" 
      :pregunta="pregunta" 
      v-model="respuesta" 
    />
    <EncuestaTexto 
      v-else-if="pregunta.type === 'TEXT'" 
      :pregunta="pregunta" 
      v-model="respuesta" 
    />
  </div>
</template>

<script>
import OpcionMultiple from './OpcionMultiple.vue';
import EncuestaTexto from './EncuestaTexto.vue';

export default {
  components: {
    OpcionMultiple,
    EncuestaTexto
  },
  props: {
    pregunta: {
      type: Object,
      required: true
    },
    modelValue: {
      type: [String, Array],
      default: ""
    }
  },
  emits: ['update:modelValue'],
  computed: {
    respuesta: {
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
