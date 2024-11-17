<template>
  <div>
    <h1>Tienda 32 BITS</h1>
    <h2> Lista de juegos</h2>
    <table border="1">
      <thead>
        <tr>
          <th>Código</th>
          <th>Nombre</th>
          <th>Stock</th>
          <th>Precio</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="juego in juegos" :key="juego.codigo">
          <td>{{ juego.codigo }}</td>
          <td>{{ juego.nombre }}</td>
          <td>{{ juego.stock }}</td>
          <td>${{ juego.precio }}</td>
          <td>
            <button @click="modificarStock(juego.codigo, -1)">-</button>
            <button @click="modificarStock(juego.codigo, 1)">+</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>



<script>

import { mapState, mapActions } from 'vuex';

export default {
  computed: {
    ...mapState(['juegos'])
  },
  methods: {
    ...mapActions(["cambiarStock"]),
    modificarStock(codigo, cantidad) {
      this.cambiarStock({ codigo, cantidad });
    }
  }
}
</script>


<style>
body {
  font-family: 'Arial', sans-serif;
  background-color: #f4f4f9;
  margin: 0;
  padding: 20px;
  color: #333;
}

h1 {
  font-family: 'Press Start 2P', cursive; 
  font-size: 24px;
  text-align: center;
  color: #adf700; 
  text-shadow: 
    0 0 5px #00ff00, 
    0 0 10px #00ff00, 
    0 0 20px #00ff00, 
    0 0 40px #0dff87, 
    0 0 80px #0dff87;
  margin-bottom: 20px;
}
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

h2 {
  text-align: center;
  margin-bottom: 20px;
}


table {
  width: 100%;
  border-collapse: collapse;
  margin: 20px 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  background-color: white;
}

th, td {
  padding: 10px 15px;
  text-align: center;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #000b3d;
  color: white;
  text-transform: uppercase;
  font-size: 14px;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: #f1f1f1;
}

button {
  background-color: #4CAF50;
  color: white;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
  border-radius: 4px;
  font-size: 14px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #45a049;
}

button:active {
  background-color: #388e3c;
}

button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

div {
  max-width: 900px;
  margin: 0 auto;
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}
</style>
