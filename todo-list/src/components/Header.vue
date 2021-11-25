<template>
    <header>
        <h1>{{ title }}</h1>
        <Button
            text="Add Task"
            color="green"
            @show-add-task-form="$emit('show-add-task-form')"
        />
    </header>
</template>
<script>
import Button from "./Button.vue";
export default {
    name: "Header",
    components: { Button },
    props: {
        title: {
            type: String,
            default: "Havn't title",
        },
    },
    emits: ["show-add-task-form"],
};
</script>
<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>
