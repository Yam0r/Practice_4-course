<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";

const students = ref([]);
onMounted(() => {
  axios.get("http://34.82.81.113:3000/students").then((response) => {
    students.value = response.data;
  });
});
</script>

<template>
  <table class="w-full border-3 text-left">
    <thead class="border-b bg-slate-300">
      <tr>
        <th>Name</th>
        <th>Group</th>
      </tr>
    </thead>
    <tbody class="bg-slate-100">
      <tr class="border-2" v-for="(stud, index) in students" :key="index">
        <td class="px-6 py-4">{{ stud.name }}</td>
        <td>{{ stud.group }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
