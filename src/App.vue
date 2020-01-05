<template>
  <div id="app">

    <h1>Bomb Assistant</h1>

    <div class="bomb_input">
      <label for="serial">Serial Number </label>
      <input type="text" id="serial" v-model="bombInfo.serial"/>
    </div>

    <div class="bomb_input">
      <label for="batteries">Number of Batteries </label>
      <input type="number" id="batteries" v-model="bombInfo.batteries"/>
    </div>

    <div class="bomb_input">
      <label for="indicator_car">Indicator CAR </label>
      <input type="checkbox" id="indicator_car" v-model="bombInfo.indicator_car"/>
    </div>

    <div class="bomb_input">
      <label for="indicator_frk">Indicator FRK </label>
      <input type="checkbox" id="indicator_frk" v-model="bombInfo.indicator_frk"/>
    </div>

    <div class="bomb_input">
      <label for="port_parallel">Parallel Port </label>
      <input type="checkbox" id="port_parallel" v-model="bombInfo.port_parallel"/>
    </div>

    <Component
            v-for="module in modules"
            :key="module.id"
            :is="module.name"
            :bombInfo="bombInfo"
    />

    <div id="buttons">
      <button
              v-for="module in avaliableModules"
              :key="module"
              @click="modules.push({id:modules.length,name:module})">
        +{{module}}
      </button>
    </div>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ModulePassword from "@/components/ModulePassword";
import ModuleCableSequence from "@/components/ModuleCableSequence";

export default {
  name: 'app',
  components: {
    ModulePassword,
    ModuleCableSequence,
    HelloWorld
  },
  data() {
    return {
      modules: [],
      avaliableModules: ["ModulePassword","ModuleCableSequence"],
      bombInfo: {
        serial: "",
        batteries: 0,
        port_parallel: false,
        indicator_car: false,
        indicator_frk: false
      },
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

  .bomb_input {
    margin: 1em;
  }

  #buttons {
    margin: 1em;
  }

  .module {
    border: solid black 2px;
    border-radius: 5px;
    margin: 1em auto;
    padding: 1em;
    width: max-content;
  }
</style>
