<template>
     <!-- start of Interview tag -->
    <CollectionInterviewMain :InterViewUrl="InterViewUrl" :url="url"/>
     <!-- End of Interview tag -->
</template>
<script setup lang="ts">
//importing the Interview url and url
let InterViewUrl="https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/?offset=0&limit=100&sort_column=id&sort_direction=desc"
let url="https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews"
</script>