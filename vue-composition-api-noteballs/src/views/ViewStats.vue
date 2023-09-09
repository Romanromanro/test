<template>
  <div class="notes">
    <table class="table is-fullwidth">
      <thead>
      <tr>
        <th>Stat</th>
        <th>Value</th>
      </tr>
      </thead>
      <tbody>
      <tr>
        <td>Number of Notes</td>
        <td>{{ storeNotes.totalNotesCount }}</td>
      </tr>
      <tr>
        <td>Number of Character (of all notes)</td>
        <td>{{ storeNotes.totalCharactersCount }}</td>
      </tr>
      </tbody>
    </table>
    <input
        class="input"
        type="text"
        placeholder="Do you love notebolls"
        v-autofocus
        v-model="loveNoteBalls"
    />
  </div>
</template>

<script setup>
import {useStoreNotes} from "@/stores/storeNotes";
import { vAutofocus } from "@/diractives/vAutofocus"
import { useWatchCharacters } from '@/use/useWatchCharacters'
import {ref} from "vue";



const storeNotes = useStoreNotes()
const loveNoteBalls = ref()
useWatchCharacters(loveNoteBalls, 50)
</script>

<style scoped>

</style>