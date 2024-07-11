<template>
  <main class="container-fluid">
    <div class="row">
      <section class="col" id="mainForm">
        <form class="p-5">
          <div class="mb-3">
            <label for="fondo" class="form-label">Color de fondo</label>
            <input type="text" class="form-control" id="fondo" v-model="fondo">
          </div>
          <div class="mb-3">
            <label for="colorTexto" class="form-label">Color de Texto</label>
            <input type="text" class="form-control" id="colorTexto" v-model="colorTexto">
          </div>
          <div class="form-check mb-3">
            <input class="form-check-input" type="checkbox" value="" id="mostrar" v-model="mostrarTexto">
            <label class="form-check-label" for="mostrar">
              Mostrar texto
            </label>
          </div>
          <div class="mb-3">
            <label for="borde" class="form-label">Borde</label>
            <input type="range" class="form-range" id="borde" v-model="borde" min="0" max="50">
          </div>
          <div class="mb-3">
            <label for="contenido" class="form-label">Contenido</label>
            <textarea class="form-control" id="contenido" rows="3" v-model="contenido"></textarea>
          </div>
          <div class="mb-3">
            <select class="form-select" aria-label="Default select example" v-model="tipografiaSeleccionada">
              <option disabled selected>Selecciona una tipografia</option>
              <option :value="tipografia.nombre" v-for="tipografia in tipografias" :key="tipografia.id">{{
                tipografia.nombre }}</option>
            </select>
          </div>
          <div class="form-check mb-3">
            <input class="form-check-input" type="checkbox" value="" id="opaco" v-model="opaco">
            <label class="form-check-label" for="opaco">
              Opaco
            </label>
          </div>
          <div class="mb-3">
            <div class="form-check">
              <input class="form-check-input" type="radio" name="pequeno" id="pequeno" value="20px"
                v-model="tamanoLetra">
              <label class="form-check-label" for="pequeno">
                Pequeño
              </label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="mediano" id="mediano" value="32px" checked
                v-model="tamanoLetra">
              <label class="form-check-label" for="mediano">
                Mediano
              </label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="grande" id="grande" value="48px"
                v-model="tamanoLetra">
              <label class="form-check-label" for="grande">
                Grande
              </label>
            </div>
          </div>
        </form>
      </section>

      <!-- Cuadro resultado -->
      <section class="col d-flex align-items-center justify-content-center">
        <div id="result" :style="{ backgroundColor: fondo, borderRadius: `${borde}%` }">
          <p v-if="mostrarTexto" :style="{ color: colorTexto, fontFamily: tipografiaSeleccionada, fontSize: tamanoLetra }"
            :class="{ opacoClass: opaco }">{{ contenido }}</p>
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
      fondo: 'darkgreen',
      colorTexto: '',
      mostrarTexto: true,
      borde: '0',
      contenido: '',
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
      ],
      tipografiaSeleccionada: '',
      opaco: false,
      tamanoLetra: '32px'
    }
  }
}
</script>

<style>
#mainForm {
  background-color: rgb(0, 51, 54);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

#result {
  min-height: 500px;
  width: 500px;
  display: grid;
  place-content: center;
}

.opacoClass {
  opacity: 0.5;
}
</style>
