<script setup>

const props = defineProps([ 'name', 'image' ])
console.log(props)

</script>

<template>
    <n-card :title="props.name">
        <template #cover>
            <img :src="props.image">
        </template>
        <slot></slot>
    </n-card>
</template>

<style scoped>
.n-card {
    width: 200px;
    margin:10px 20px;
}

.n-card-header {
    padding-bottom: 0 !important;
}

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}
</style>