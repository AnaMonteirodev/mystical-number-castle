
<template>
  <div id="app">
    <!-- Otimizador de performance -->
    <PerformanceOptimizer />
    
    <!-- Efeitos atmosféricos (névoa e estrelas) -->
    <AtmosphericEffects />
    
    <!-- Sistema de partículas (vagalumes) -->
    <ParticleSystem />
    
    <!-- Tela de reunião -->
    <MeetingScreen v-if="gameStore.currentScreen === 'meeting'" />
    
    <!-- Tela de jogo com animação de entrada -->
    <GameScreenEntrance v-if="gameStore.currentScreen === 'game' && gameStore.isInGameEntrance">
      <GameScreen />
    </GameScreenEntrance>
    
    <!-- Tela de jogo normal (sem animação) -->
    <GameScreen v-if="gameStore.currentScreen === 'game' && !gameStore.isInGameEntrance" />
    
    <!-- EndingScreen será adicionado na Fase 4 -->
    
    <!-- Debug Panel (temporário) -->
    <DebugPanel />
  </div>
</template>

<script setup>
import { useGameStore } from './stores/gameStore';
import MeetingScreen from './views/MeetingScreen.vue';
import GameScreen from './views/GameScreen.vue';
import ParticleSystem from './components/ParticleSystem.vue';
import AtmosphericEffects from './components/AtmosphericEffects.vue';
import PerformanceOptimizer from './components/PerformanceOptimizer.vue';
import GameScreenEntrance from './components/GameScreenEntrance.vue';
import DebugPanel from './components/DebugPanel.vue';

const gameStore = useGameStore();
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  height: 100vh;
  overflow: hidden;
}


</style>

