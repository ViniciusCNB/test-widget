<script setup>
// Componente simplificado para testar widgets via iframe
</script>

<template>
  <div class="container">
    <header>
      <h1>Teste de Widget</h1>
      <p>Use este iframe para testar seu widget externo</p>
    </header>

    <main>
      <div class="iframe-container">
        <iframe 
          id="widget-iframe"
          src="" 
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
        ></iframe>
      </div>
      
      <div class="controls">
        <input 
          v-model="token" 
          type="text" 
          placeholder="Token" 
          class="url-input"
        />
        <button @click="updateIframe" class="load-btn">Carregar</button>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      token: '',
    }
  },
  methods: {
    updateIframe() {
      if (this.token) {
        document.getElementById('widget-iframe').src = `http://localhost:3000/widget?token=${this.token}`;
      }
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  color: #333;
  background-color: #f4f4f4;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

header {
  text-align: center;
  margin-bottom: 30px;
}

h1 {
  margin-bottom: 10px;
  color: #2c3e50;
}

.iframe-container {
  background-color: #fff;
  border: 2px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 20px;
  height: 70vh;
  width: 1200px;
}

iframe {
  width: 100%;
  height: 100%;
}

.controls {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.url-input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
}

.load-btn {
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s;
}

.load-btn:hover {
  background-color: #3ca876;
}
</style>
