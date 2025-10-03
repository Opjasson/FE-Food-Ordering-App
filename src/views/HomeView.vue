<template>
    <div></div>
</template>
<script setup>
import router from "@/router";
import { onMounted } from "vue";

const userName = localStorage.getItem("name");
onMounted(() => {
    if (userName == null) {
        router.push("login");
    }
});
</script>
<style></style>
