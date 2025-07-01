<script setup lang="ts">

</script>

<template>
  <div class="formulario">
    <h1>Crear Usuario</h1>

    <form @submit.prevent="crearUsuario">
      <label>
        Nombre de usuario:
        <input type="text" v-model="nombre" required />
      </label>

      <label>
        Email:
        <input type="email" v-model="email" required />
      </label>

      <label>
        Contraseña:
        <input type="password" v-model="password" required />
      </label>

      <label>
        Fecha de nacimiento:
        <input type="date" v-model="fechaNacimiento" required />
      </label>

      <button type="submit">Crear Usuario</button>
    </form>

    <!-- OPCIONAL: mostrar datos a medida que se completan -->
    <div v-if="nombre || email || password || fechaNacimiento">
      <h2>Vista previa:</h2>
      <p><strong>Nombre:</strong> {{ nombre }}</p>
      <p><strong>Email:</strong> {{ email }}</p>
      <p><strong>Fecha de nacimiento:</strong> {{ fechaNacimiento }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      email: '',
      password: '',
      fechaNacimiento: ''
    };
  },
  methods: {
    calcularEdad(fecha) {
      const nacimiento = new Date(fecha);
      const hoy = new Date();
      let edad = hoy.getFullYear() - nacimiento.getFullYear();
      const m = hoy.getMonth() - nacimiento.getMonth();
      if (m < 0 || (m === 0 && hoy.getDate() < nacimiento.getDate())) {
        edad--;
      }
      return edad;
    },
    crearUsuario() {
      const usuario = {
        nombre: this.nombre,
        email: this.email,
        password: this.password,
        fechaNacimiento: this.fechaNacimiento,
        edad: this.calcularEdad(this.fechaNacimiento)
      };

      alert(`Usuario creado con éxito:\nNombre: ${usuario.nombre}\nEmail: ${usuario.email}\nEdad: ${usuario.edad}`);

      // Limpiar formulario
      this.nombre = '';
      this.email = '';
      this.password = '';
      this.fechaNacimiento = '';
    }
  }
};
</script>

<style scoped>
.formulario {
  max-width: 400px;
  margin: auto;
  padding: 1rem;
  border-radius: 10px;
  background-color: #f3f3f3;
  font-family: sans-serif;
}
label {
  display: block;
  margin-top: 1rem;
}
input {
  width: 100%;
  padding: 0.5rem;
  margin-top: 0.25rem;
}
button {
  margin-top: 1rem;
  padding: 0.5rem 1rem;
}
</style>
