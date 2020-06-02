<template>
<div>
<div class="Logs" v-for="Log in Logs" :key="Log.id"> 
{{ Log.log }}
</div>
</div>
</template>

<script>
export default {
  name: 'Logs',
  props: {
    Logs: Array
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Chelsea+Market&display=swap');
.Logs{
  color: gray;
  margin: 1rem;
}
img {
  max-width: 100px;
}
#sp {
  max-width: 50px;
  margin: 0 1rem;
}
</style>