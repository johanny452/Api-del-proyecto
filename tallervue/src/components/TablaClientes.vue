<template>
    <div class="container">
        <h1>Tabla de clientes</h1>
        <table>
            <thead>
                <tr>
                    <th>Cedula</th>
                    <th>Nombre</th>
                    <th>Apellido</th>
                    <th>Direccion</th>
                    <th>Correo</th>
                    <th>Telefono</th>
                    
                </tr>
            </thead>
            <tbody>
              
                    <tr v-for="clientes in  clientes" :key="clientes.cedula">
                    <td>{{ clientes.cedula }}</td>
                    <td>{{ clientes.nombre }}</td>
                    <td>{{ clientes.apellido }}</td>
                    <td>{{ clientes.direccion }}</td>
                    <td>{{ clientes.correo }}</td>
                    <td>{{ clientes.telefono }}</td>
                </tr>
                   
                <router-view />
            
              
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      clientes: [],
    };
  },
  methods: {
    obtenerClientes() {
   
      axios.get("http://localhost:8080/api/clientes/listar")
      .then((response) => {
        this.clientes = response.data;
      })
      .catch((error) => {
        console.error("Error al obtener clientes:", error);
      });
    },
  },
  mounted() {
    
    this.obtenerClientes();
  },
};
</script>
