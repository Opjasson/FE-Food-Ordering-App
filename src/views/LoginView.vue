<template>
    <div
        class="bg-light d-flex justify-content-center align-items-center vh-100">
        <div class="card shadow p-4" style="width: 350px; border-radius: 1rem">
            <h3 class="text-center mb-3">Login</h3>
            <form @submit.prevent>
                <!-- Email -->
                <div class="mb-3">
                    <p></p>
                    <label for="email" class="form-label">Email address</label>
                    <input
                        type="email"
                        class="form-control"
                        id="email"
                        placeholder="Enter email"
                        required
                        v-model="formData.email" />
                </div>
                <!-- Password -->
                <div class="mb-3">
                    <label for="password" class="form-label">Password</label>
                    <input
                        type="password"
                        class="form-control"
                        id="password"
                        placeholder="Enter password"
                        required
                        v-model="formData.password" />
                </div>
                <p class="text-danger">{{ msgErr }}</p>
                <!-- Submit -->
                <button @click="login" class="btn btn-primary w-100">
                    Login
                </button>
            </form>
            <p class="text-center mt-3 mb-0">
                <a href="#">Forgot password?</a>
            </p>
        </div>
    </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";

const formData = ref({
    email : "",
    password : ""
});

const msgErr = ref(null)




async function login() {
    msgErr.value = null
    try {
        const response = await axios.post("http://127.0.0.1:8000/api/auth/login", formData.value);
        console.log(response.data);
    } catch (error) {
        console.log(error);
        msgErr.value = error.response.data.message
    }
}
</script>

<style lang="scss" scoped></style>
