<script setup>
defineProps(['prev','next','inicio','fin','count']);
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button type="button" class="btn btn-primary" @click="prev" :disabled="inicio <= 0">Preview</button>
        <button type="button" class="btn btn-primary" @click="next" :disabled="fin >= count">Next</button>
    </div>
</template>