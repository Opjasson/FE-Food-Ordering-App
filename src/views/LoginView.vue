<template>
    <div
        class="bg-light d-flex justify-content-center align-items-center vh-100">
        <div class="card shadow p-4" style="width: 350px; border-radius: 1rem">
            <h3 class="text-center mb-3">Login</h3>
            <form @submit.prevent>
                <!-- Email -->
                <div class="mb-3">
                    <label for="email" class="form-label">Email address</label>
                    <input
                        type="email"
                        class="form-control"
                        id="email"
                        placeholder="Enter email"
                        required
                        v-model="email" />
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
                        v-model="password" />
                </div>
                <!-- Remember Me -->
                <div class="mb-3 form-check">
                    <input
                        type="checkbox"
                        class="form-check-input"
                        id="rememberMe" />
                    <label class="form-check-label" for="rememberMe"
                        >Remember me</label
                    >
                </div>
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
import { ref } from "vue";

const email = ref("");
const password = ref("");

function login() {
    console.log(email.value);
    console.log(password.value);
}
</script>

<style lang="scss" scoped></style>
