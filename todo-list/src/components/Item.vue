<template>
    <div
        :class="['task-item', item.reminder && 'task-reminder']"
        @click="$emit('toggle-reminder', item)"
    >
        <h3>
            {{ item.info }}
            <font-awesome-icon
                :icon="['fa', 'times']"
                @click="$emit('delete-item', item.id)"
            />
        </h3>
        <p>{{ item.day }}</p>
    </div>
</template>
<script>
export default {
    props: {
        item: Object,
    },
};
</script>
<style scoped>
.fas {
    color: red;
}
.task-item {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
.task-item.task-reminder {
    border-left: 5px solid green;
}
.task-item h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>
