<template>
  
    <table>
      <tr>
        <td>
          <img :src="imag1" alt=" no encontrado" />
        </td>
        <td>
          <img :src="imag2" alt="no encontrado" />
        </td>
        <td>
          <img :src="imag3" alt="no encontrado" />
        </td>
      </tr>
      <tr>
        <td>
          <p>{{ nombre1 }}</p>
        </td>
        <td>
          <p>{{ nombre2 }}</p>
        </td>
        <td>
          <p>{{ nombre3 }}</p>
        </td>
      </tr>
    </table>
  
</template>

<script>
export default {
props: {
    nombre1: {
      type: String,
      required: true,
    },
    nombre2: {
      type: String,
      required: true,
    },
    nombre3: {
      type: String,
      required: true,
    },
    imag1:{
      type: String,
      required: true,  
    } ,
    imag2:{
      type: String,
      required: true,  
    } ,
    imag3:{
      type: String,
      required: true,  
    } 
  }
}
</script>

<style scoped>
img {
  width: 200px;
  height: 200px;
  margin-left: 20px;
}
table {
  margin: auto;
}
p{
    font-family: 'Times New Roman', Times, serif;
    font-size: large;
    font-weight: bold;
    color: black;
}
</style>