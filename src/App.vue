<template>
  <div>
    <Beverage :isIced="currentTemp === 'Cold'" :creamer="currentCreamer.id !== 'c1'" :syrup="currentSyrup.id !== 's1'"/>
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="base in bases" :key="base.id">
          <label>
            <input
              type="radio"
              name="base.name"
              :id="base.id"
              :value="base"
              v-model="currentBase"
            />
            {{ base.name }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="cream in creamers" :key="cream.id">
          <label>
            <input
              type="radio"
              name="cream.name"
              :id="cream.id"
              :value="cream"
              v-model="currentCreamer"
            />
            {{ cream.name }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="syrup in syrups" :key="syrup.id">
          <label>
            <input
              type="radio"
              name="syrup.name"
              :id="syrup.id"
              :value="syrup"
              v-model="currentSyrup"
            />
            {{ syrup.name }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import { temps, currentTemp, currentBase, currentCreamer, currentSyrup, bases, creamers, syrups } from "./stores/beverage";
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
