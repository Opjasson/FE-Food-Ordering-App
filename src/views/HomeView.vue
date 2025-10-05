<template>
    <Navbar :name="userName" />
    <h1>Hallo</h1>
</template>
<script setup>
import router from "@/router";
import { onMounted } from "vue";
import Navbar from "@/components/Navbar.vue";

const userName = localStorage.getItem("name");
onMounted(() => {
    if (userName == null || !userName || userName == "") {
        router.push("login");
    }
});
</script>
<style></style>
