<template>
  <main class="container-fluid">
    <div class="row">
      <!-- Seccion del formulario -->
      <section class="col" id="mainForm">
        <form class="p-5">
          <div class="mb-3">
            <label for="fondo" class="form-label">Color de fondo</label>
            <input type="text" class="form-control" id="fondo" v-model="fondo">
          </div>
          <div class="mb-3">
            <label for="colorTexto" class="form-label">Color de texto</label>
            <input type="text" class="form-control" id="colorTexto" v-model="colorTexto">
          </div>
          <div class="form-check mb-3">
            <input type="checkbox" id="mostrar" class="form-check-input" v-model="mostrarTexto">
            <label for="mostrar" class="form-check-label">Mostrar texto</label>
          </div>
          <div class="mb-3">
            <label for="borde" class="form-label">Borde</label>
            <input type="range" class="form-range" id="borde" min="0" max="50" v-model="borde">
          </div>
          <div class="mb-3">
            <label for="contenido" class="form-label">Contenido</label>
            <textarea class="form-control" id="contenido" rows="3" v-model="contenido"></textarea>
          </div>
          <div class="mb-3">
            <select class="form-select" id="tipografia" v-model="tipografiaSeleccionada">
              <option disabled selected value="">Selecciona una tipografía</option>
              <option v-for="tipografia in tipografias" :key="tipografia.id" :value="tipografia.nombre">{{
                tipografia.nombre }}</option>
            </select>
          </div>
          <div class="form-check mb-3">
            <input type="checkbox" id="opaco" class="form-check-input" v-model="opaco">
            <label for="opaco" class="form-check-label">Opaco</label>
          </div>
          <div class="mb-3">
            <div class="form-check">
              <input type="radio" id="pequeno" value="20px" class="form-check-input" v-model="tamanoLetra">
              <label for="pequeno" class="form-check-label">Pequeño</label>
            </div>
            <div class="form-check">
              <input type="radio" id="mediano" value="32px" class="form-check-input" v-model="tamanoLetra">
              <label for="mediano" class="form-check-label">Mediano</label>
            </div>
            <div class="form-check">
              <input type="radio" id="grande" value="48px" class="form-check-input" v-model="tamanoLetra">
              <label for="grande" class="form-check-label">Grande</label>
            </div>
          </div>
        </form>
      </section>

      <!-- Seccion del resultado -->
      <section class="col d-flex justify-content-center align-items-center">
        <div id="result" :style="{backgroundColor: fondo, borderRadius: `${borde}%`}">
          <p v-if="mostrarTexto" :style="{color: colorTexto, fontFamily: tipografiaSeleccionada, fontSize: tamanoLetra}" :class="{opacoClass: opaco}">{{ contenido }}</p>
        </div>
      </section>
    </div>
  </main>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      // estados formulario
      fondo: 'darkgreen',
      colorTexto: 'white',
      mostrarTexto: true,
      borde: '0',
      contenido: '',
      opaco: false,
      tamanoLetra: '32px',
      tipografiaSeleccionada: '',

      // otros
      tipografias: [
        {
          id: '1',
          nombre: 'Roboto'
        },
        {
          id: '2',
          nombre: 'Montserrat'
        },
        {
          id: '3',
          nombre: 'Open Sans'
        },
        {
          id: '4',
          nombre: 'Arial'
        }
      ]
    }
  }
}
</script>

<style>
.opacoClass {
  opacity: 0.5;
}

#mainForm {
  background-color: rgb(0,51,54);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

#result {
  min-height: 500px;
  width: 500px;
  display: grid;
  place-content: center
}
</style>
