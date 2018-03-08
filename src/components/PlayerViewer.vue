<template>
   <iframe width="100%" height="400" :src="movie.trailer" controls></iframe>
</template>

<script>

export default {
  name: 'PlayerViewer',
  props: {
    movie : { type: Object, required: false}
  }
}
</script>