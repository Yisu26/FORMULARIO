<template>
    <div class="container">
        <h1>¡BIENVENIDO!</h1>
        <div class="gif-container">
          <iframe 
           src="https://giphy.com/embed/fnmsu2lTw3r1e" 
           width="462" 
           height="480" 
           frameborder="0" 
           class="giphy-embed" 
           allowfullscreen>
          </iframe>
          <p><a href="https://giphy.com/gifs/artists-on-tumblr-dinosaur-dinosaurs-fnmsu2lTw3r1e">via GIPHY</a></p>
        </div>
    </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({

    name: 'Home'
    
    
    })
</script>

<style scoped>
.gif-container {
  text-align: center;
  margin-top: 20px;
}

.giphy-embed {
  border-radius: 10px;
}
</style>