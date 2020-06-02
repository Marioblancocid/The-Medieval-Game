<template>
<div>
  <div class="about">
    <h1>Mario Blanco Cid</h1>
    <img src="../assets/images/0.jpeg" alt="Imagen de Mario Blanco">
    <p>
      <strong>Status:</strong> alive
    </p>
    <p>
      <strong>Gender:</strong> Male
    </p>
    <p>
      <strong>Specie:</strong> Coder
    </p>
    <p>
      <strong>Origin:</strong> Ourense - Galicia
    </p>
    <p>
      Este proyecto ha sido creado por <a href="https://www.linkedin.com/in/mario-blanco-cid-62098519b/" alt="Enlace al LinkedIn de Mario Blanco">Mario</a>
    </p>
  </div>
</div>
</template>

<script>
export default {
  name: 'About',
  created() {
    document.title = "About | MedievalGame";
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bangers&display=swap');
img {
  border-radius: 50%;
  border: 10px solid rgba(2, 46, 66, 0.404);
  min-width: 50%;
  max-width: 50%;
}
.about {
  min-width: 80%;
  max-width: 80%;
  border-radius: 2rem;
  border: 5px solid rgba(2, 46, 66, 0.404);
  background: rgb(15, 176, 200);
  color: white;
  margin: 1rem;
  display: inline-block;
  background: rgb(62, 37, 129);
  font-family: 'Bangers', cursive;
  font-size: 1rem;
  letter-spacing: 3px;
}
strong {
  color: black;
  text-shadow: -1px 0 white, 0 1px white, 1px 0 white, 0 -1px white;
}
a {
  color: white
}

@media (min-width: 600px) {
img {
  min-width: 50%;
  max-width: 50%;
  border: 5px solid rgba(2, 46, 66, 0.404);
}
.about {
  min-width: 470px;
  max-width: 470px;
  min-height: 450px;
}
p {
  margin: 0.5rem;
  font-size: 1.2rem;
}
h1 {
  margin: 1rem
}
}

</style>
