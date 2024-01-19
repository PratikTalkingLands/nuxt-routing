<template>
    <p>{{ user }}</p>
</template>

<script setup>
import { useAttrs } from 'vue';

const user = useAttrs().user
</script>