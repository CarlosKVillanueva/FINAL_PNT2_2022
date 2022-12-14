<template>

  <section class="src-components-conversor-pesos-dolares">
    <h1>Conversor de Divisa</h1>
    <label for="pesos">Ingrese monto a convertir $</label>
    <input
        type="number"
        name="pesos"
        id="pesos"
        v-model.number="cantPesos">
    <br>
    <br>
    <label for="dolares">Valor dólar en $</label>
    <input
        type="number"
        name="dolares"
        id="dolares"
        v-model.number="precioDolar">
    <label for="checkBoxUpdate"> - Actualización</label>
    <input
        type="checkbox"
        name="checkBoxUpdate"
        id="checkBoxUpdate"
        v-model="inputCheckbox">
    <span v-if="inputCheckbox">{{ this.getFecha }} Cotizacion Dolar a la Fecha: {{ this.cotizacionDolar }}</span>
    <p>Valor convertido USD {{ this.calcularCotizacion }}</p>

    <div>
      <h1>Respuestas Choice</h1>
      <ol>
        <li>c</li>
        <li>b</li>
        <li>c</li>
        <li>a</li>
        <li>d</li>
      </ol>
    </div>
  </section>



</template>

<script>

export default  {
  name: 'src-components-conversor-pesos-dolares',
  props: [],
  mounted () {},
  data () {
    return {
      precioDolar: undefined,
      cantPesos: undefined,
      inputCheckbox: false,
      urlApiCotizacion: 'https://www.dolarsi.com/api/api.php?type=valoresprincipales',
      cotizacionDolar: undefined
    }
  },

  methods: {
    async dolarTiempoReal() {
      const { data } = await this.axios(this.urlApiCotizacion);
      let cantidad = data[1].casa.compra
      this.cotizacionDolar = cantidad
      return cantidad * 1
    },
  },
  computed: {
    calcularCotizacion(){
      let cantidad
      if (this.inputCheckbox) {
        cantidad = this.cantPesos / this.cotizacionDolar
      } else {
        cantidad = this.precioDolar > 0 ? this.cantPesos / this.precioDolar : 0
      }
      console.log(typeof cantidad)
      return cantidad

    },
    getFecha() {
      return new Date().toISOString()
    },
  }
}


</script>

<style scoped lang="css">
</style>