<template>
<h1>JUEGO CASINO POKEMON</h1>
  <div>
    <h1 class="enLinea" v-if="visibleContenido">Puntos: {{ puntos }}</h1>
    <h1 class="enLinea" v-if="visibleContenido">Intento:{{ Intentos }}</h1>
  </div>
  <picture-pokemon-vue
    v-if="visibleContenido"
    :imag1="imagen"
    :nombre1="nom"
    :imag2="imagen2"
    :nombre2="nom2"
    :imag3="imagen3"
    :nombre3="nom3"
  ></picture-pokemon-vue>

  <img v-if="visibleImagen" src="../assets/congratulations.gif" alt="" />
  <p v-if="visibleMensaje">{{ mensaje }}</p>
  <br>
  <br>
  <div>
    <button v-if="visibleContenido" v-on:click="obtenerPokemon">JUGAR</button>
    <button v-if="visibleMensaje" v-on:click="nuevoJuego">Nuevo Juego</button>
  </div>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>

</template>

<script>
import picturePokemonVue from "./picturePokemon.vue";
import obtenerPokemonsOpciones from "../helpers/metodoPokemon";
export default {
  components: {
    picturePokemonVue,
  },
  data() {
    return {
      puntos: 0,
      Intentos: 0,
      imagen:
        "https://upload.wikimedia.org/wikipedia/commons/6/62/Color_negro.jpg",
      nom: "xxxxxxxxxx",
      imagen2:
        "https://upload.wikimedia.org/wikipedia/commons/6/62/Color_negro.jpg",
      nom2: "xxxxxxxxxx",
      imagen3:
        "https://upload.wikimedia.org/wikipedia/commons/6/62/Color_negro.jpg",
      nom3: "xxxxxxxxxx",
      visibleContenido: true,
      visibleMensaje: false,
      visibleImagen: false,
      mensaje: null,
    };
  },
  methods: {
    async obtenerPokemon() {
      const arrayP = await obtenerPokemonsOpciones();
      this.nom = arrayP[0].nombre;
      this.imagen = arrayP[0].ima;
      this.nom2 = arrayP[1].nombre;
      this.imagen2 = arrayP[1].ima;
      this.nom3 = arrayP[2].nombre;
      this.imagen3 = arrayP[2].ima;
      if (this.Intentos <= 5) {
        if (arrayP[0].id == arrayP[1].id && arrayP[0].id == arrayP[2].id) {
          this.puntos = this.puntos + 5;
          this.Intentos += 1;
        } else if (
          arrayP[0].id == arrayP[1].id ||
          arrayP[0].id == arrayP[2].id ||
          arrayP[1].id == arrayP[2].id
        ) {
          this.puntos = this.puntos + 2;
          this.Intentos += 1;
        } else {
          this.Intentos += 1;
        }
        if (this.puntos >= 10) {
          this.visibleContenido = false;
          this.mensaje = `"Felicitaciones has ganado un premio de $10.000,00"`;
          this.visibleMensaje = true;
          this.visibleImagen = true;
        }
      }

      if (this.Intentos == 6) {
        this.visibleContenido = false;
        this.mensaje = `"El juego ha terminado y no ha ganado ningún premio"`;
        this.visibleMensaje = true;
        this.visibleImagen = false;
      }
    },
    nuevoJuego() {
      this.visibleContenido = true;
      this.imagen =
        "https://upload.wikimedia.org/wikipedia/commons/6/62/Color_negro.jpg";
      this.imagen2 =
        "https://upload.wikimedia.org/wikipedia/commons/6/62/Color_negro.jpg";
      this.imagen3 =
        "https://upload.wikimedia.org/wikipedia/commons/6/62/Color_negro.jpg";
      this.nom = "xxxxxxxxxx";
      this.nom2 = "xxxxxxxxxx";
      this.nom3 = "xxxxxxxxxx";
      this.puntos = 0;
      this.Intentos = 0;
      this.visibleMensaje = false;
      this.visibleImagen = false;
    },
  },
};
</script>

<style scoped>
div {
  justify-content: center;
}

button {
  width: 200px;
  height: 50px;
  border: 5px solid black;
  background-color: rgb(17, 160, 48);
  font-weight: bold;
  font-family: "Times New Roman", Times, serif;
}
.enLinea{
  display: inline;
  margin: 50px;
  
}
h1 {
  
  font-family: "Times New Roman", Times, serif;
  font-size: 30px;
  font-weight: bold;
  color: black;
  margin:10px;
}
p {
  
  font-family: "Times New Roman", Times, serif;
  font-style: oblique;
  color: black;
  margin-bottom:30px
}
</style>