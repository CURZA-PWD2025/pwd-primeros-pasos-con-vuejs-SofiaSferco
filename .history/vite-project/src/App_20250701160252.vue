

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

    
    <div v-if="nombre || email || password || fechaNacimiento">
      <h2>Vista previa:</h2>
      <p><strong>Nombre:</strong> {{ nombre }}</p>
      <p><strong>Email:</strong> {{ email }}</p>
      <p><strong>Fecha de nacimiento:</strong> {{ fechaNacimiento }}</p>
    </div>
  </div>
</template>



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
