<script lang="ts" setup>
import {Snowflake} from 'yukidaruma'
const epoch = new Date('2023-01-01').getTime()
const snowflake = new Snowflake(
  epoch,
  1, // worker id
);
const snowflakeId = ref(snowflake.generateId())
const regenerateSnowflakeId = () => {
  snowflakeId.value = snowflake.generateId()
}
</script>

<template>
  <div class="main-frame">
    <h1>Snowflake playground</h1>
    Here is new snowflake id:
    <p id="snowflake-area">
      {{ snowflakeId }}
    </p>
    <button @click="regenerateSnowflakeId" id="regenerate">Regenerate</button>
  </div>
</template>

<style scoped>
.main-frame {
  display: flex;
  flex-direction: column;
  width: 100%;
  align-items: center;
}

#regenerate{
  padding: 1em;
  width: fit-content;
}

</style>
