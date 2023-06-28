<script setup>

const props = defineProps([ 'name', 'image' ])
console.log(props)

</script>

<template>
    <n-card :title="props.name">
        <template #cover>
            <img :src="props.image">
        </template>
    </n-card>
</template>

<style scoped>
.n-card {
    width: 200px;
    margin:10px 20px;
    height: 400px;

}

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}
</style>