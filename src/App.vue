<template>
  <EncuestaPrincipal :datosEncuesta="datosEncuesta" />
</template>
<script>
import EncuestaPrincipal from './components/EncuestaPrincipal.vue';
import encuestaData from './data/datos.json'; // Importa el archivo JSON

export default {
  components: {
    EncuestaPrincipal
  },
  data() {
    return {
      // Asigna los datos del JSON a la propiedad `datosEncuesta`
      datosEncuesta: encuestaData
    };
  }
};
</script>