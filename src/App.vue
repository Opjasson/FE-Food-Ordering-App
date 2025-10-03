<script setup>
import { RouterLink, RouterView } from "vue-router";
import router from "./router";
import axios from "axios";

const userName = localStorage.getItem("name");

const logout = async () => {
    try {
        await axios.get(
            "http://127.0.0.1:8000/api/auth/logout",
            {
                headers: {
                    Authorization: `Bearer ${localStorage.getItem("token")}`,
                },
            }
        );
        localStorage.removeItem("email");
        localStorage.removeItem("name");
        localStorage.removeItem("token");
        localStorage.removeItem("roleId");
        router.push({ name: "login" });
    } catch (error) {
        console.log(error);
    }
};
</script>

<template>
    <header v-if="$route.name != 'login'">
        <nav class="navbar navbar-expand-lg bg-body-tertiary">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">JssN Cafe</a>
                <button
                    class="navbar-toggler"
                    type="button"
                    data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent"
                    aria-controls="navbarSupportedContent"
                    aria-expanded="false"
                    aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div
                    class="collapse navbar-collapse"
                    id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item me-3">
                            <RouterLink to="/">HOME</RouterLink>
                        </li>

                        <li class="nav-item">
                            <a style="cursor: pointer;" class="hoverLogout" @click="logout()"
                                >LOGOUT</a
                            >
                        </li>
                    </ul>
                    <li class="d-flex">
                        <span>Hi, {{ userName }}</span>
                    </li>
                </div>
            </div>
        </nav>
    </header>

    <!-- <nav>
        <ul>
            <li>Home</li>
            <li>About</li>
        </ul>
    </nav> -->
    <RouterView />
</template>

<style scoped>
    .hoverLogout:hover {
        color: red;
    }
</style>
