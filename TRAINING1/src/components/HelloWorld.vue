<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios';
defineProps<{ msg: string }>()

const count = ref(0);
const message = ref('');
const list = ref();
const getlish = async function () {
  const { data } = await axios.get("https://gorest.co.in/public/v2/users");
  list.value = data;
}

const add = () => {
  count.value++
}

</script>

<template>
  
  <div class="col-start2">
    <h1 class="text-center">{{ msg + '' + message }}</h1>
    <div class="card text-center">
    </div>
    <input type="text" v-model="message">
    <button type="button" class="text-white bg-gradient-to-r from-blue-500 via-blue-600 to-blue-700 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center ml-2 mr-2 mb-2" @click="getlish">Click It</button>
    <button type="button" class="text-white bg-gradient-to-r from-red-400 via-red-500 to-red-600 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-red-300 dark:focus:ring-red-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2" @click="count++">count is {{ count }}</button>
    <div v-for="(item, index) in list" :key="index">
      <div
        class="corder-gray-200 bg-white px-10 py-10 text start my-10 rounded-xl"
      >
        <h3 class="text-base font-semibold leading-6 texr-gray-900">
          Title : {{ item["title"] }}
        </h3>
        <h3 class="text-base font-semibold leading-6 texr-gray-900">
          User : {{ item["user_name"] }}
        </h3>
        <h3 class="text-base font-semibold leading-6 texr-gray-900">
          Status : {{ item["status"] }}
        </h3>
      </div>
    </div>
  </div>
  <!-- <pre>{{ list }}</pre> -->

  <!-- <div class="card">
    <input type="text" v-model="message">
    <button type="button" class="text-white bg-gradient-to-r from-blue-500 via-blue-600 to-blue-700 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center ml-2 mr-2 mb-2" @click="getlish">Click It</button>
    <button type="button" class="text-white bg-gradient-to-r from-red-400 via-red-500 to-red-600 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-red-300 dark:focus:ring-red-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div> -->

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue + Vite
    starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
