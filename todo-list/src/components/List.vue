<template>
    <div v-for="item in list_data" :key="item.id">
        <Item
            :item="item"
            @toggle-reminder="(target) => $emit('toggle-reminder', target.id)"
            @delete-item="(id) => $emit('delete-item', id)"
        />
    </div>
</template>
<script>
import Item from "../components/Item.vue";
export default {
    components: { Item },
    props: {
        list_data: Array,
    },
    emits: ["toggle-reminder"],
};
</script>
