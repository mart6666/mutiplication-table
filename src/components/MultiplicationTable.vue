<script setup>
/* All js lives here */
import InputField from "./InputField.vue";

import {ref} from "vue";

const name = ref('Nikolai')
const numOfRows = ref(10)
const numOfCols = ref(10)
const rowToHighlight = ref(1)
const columnToHighlight = ref(10)
const showTheMath = ref(false)
</script>

<template>
  <section class="container">

    <h1>My multiplication table playground</h1>

    <h2 v-if="name">Welcome {{ name }}!</h2>
    <h2 v-else>Please tell us your name</h2>

    <div class="inputs">

      <input-field label-text="What's your name?"
                   v-model="name"/>
      <input-field label-text="How many rows do you want?" input-type="number"
                   v-model="numOfRows"/>
      <InputField label-text="Which row to highlight?" input-type="number"
                  v-model="numOfCols"/>


      <input-field
        label-text="Which row to highlight?"
        input-type="number"
        min="1"
        v-model.number="rowToHighlight"/>

      <input-field
        label-text="How many columns do you want?"
        input-type="number" min="1"
        v-model.number="numOfCols"/>

      <label>
        Which column should we highlight?
        <input type="number" v-model.number="columnToHighlight"/>
      </label>

      <label>
        Show me the math?
        <input type="checkbox" v-model="showTheMath"/>
      </label>
    </div>


    <table>
      <tr v-for="row in numOfRows" :class="{ 'highlight' : row === rowToHighlight }">
        <td v-for="col in numOfCols" :class="{ 'highlight' : col === columnToHighlight }">
          {{ row * col }}

          <div v-if="showTheMath" class="show-the-math">
            {{ row }} x {{ col }}
          </div>
        </td>
      </tr>
    </table>

  </section>

</template>


<style scoped>
section.container {
  border: 10px solid black;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;

  h1, h2, h3, h4, h5, h6 {
    margin: 0;
  }

  div.inputs {
    border: 2px solid red;
    gap: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;

    label {
      display: flex;
      justify-content: space-between;
      border: 1px solid black;
      width: 100%;
    }
  }
}

table {
  border: 4px solid black;

  tr {
    &.highlight {
      background-color: blue;
      color: white;
    }

    &:hover {
      background-color: lightblue;
    }

    td {
      border: 1px dotted red;
      text-align: center;

      &.highlight {
        background-color: blue;
        color: white;
      }

      div.show-the-math {
        font-size: 10px;
      }
    }
  }
}
</style>