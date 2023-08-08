<script setup>
  import { reactive, ref } from 'vue'
  const data = reactive({
      username: '',
      password: '',
      loginUsername: '',
      loginPassword: '',
    });

    const isLoggedIn = ref(false);
    const showLogin = ref(false);

    const registerUser = () => {
      isLoggedIn.value = false;
      showLogin.value = true;
    };

    const loginUser = () => {
      data.username = data.loginUsername;
      isLoggedIn.value = true;
      showLogin.value = false;
    };

    const logout = () => {
      isLoggedIn.value = false;
    };
</script>

<template>
  <div class="bg-gray-100">
    <div class="flex justify-center items-center h-screen">
      <div class="bg-white p-8 rounded shadow w-80">
        <div v-if="!isLoggedIn && !showLogin">
          <h1 class="text-3xl font-bold mb-4">Register</h1>
          <form @submit.prevent="registerUser">
            <div class="mb-4">
              <label for="username" class="block text-gray-700">Username</label>
              <input v-model="username" type="text" id="username" class="border rounded px-4 py-2 w-full" required>
            </div>
            <div class="mb-4">
              <label for="password" class="block text-gray-700">Password</label>
              <input v-model="password" type="password" id="password" class="border rounded px-4 py-2 w-full" required>
            </div>
            <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">Register</button>
          </form>
        </div>
        <div v-if="!isLoggedIn && showLogin">
          <h1 class="text-3xl font-bold mb-4">Login</h1>
          <form @submit.prevent="loginUser">
            <div class="mb-4">
              <label for="loginUsername" class="block text-gray-700">Username</label>
              <input v-model="loginUsername" type="text" id="loginUsername" class="border rounded px-4 py-2 w-full" required>
            </div>
            <div class="mb-4">
              <label for="loginPassword" class="block text-gray-700">Password</label>
              <input v-model="loginPassword" type="password" id="loginPassword" class="border rounded px-4 py-2 w-full" required>
            </div>
            <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">Login</button>
            <button @click="showLogin = false" class="ml-4 text-blue-500">Register</button>
          </form>
        </div>
        <div v-if="isLoggedIn">
          <h1 class="text-3xl font-bold mb-4">Welcome, {{ username }}</h1>
          <button @click="logout" class="bg-red-500 text-white px-4 py-2 rounded">Logout</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
