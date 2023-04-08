<template>
    <CollectionInterviewMain :InterViewUrl="InterViewUrl" :url="url"/>
</template>
<script setup lang="ts">
let InterViewUrl="https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/?offset=0&limit=100&sort_column=id&sort_direction=desc"
let url="https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews"
</script>