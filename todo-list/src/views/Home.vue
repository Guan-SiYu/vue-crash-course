<template>
    <Form :show_add_task_form="show_add_task_form" @add-item="addItem" />
    <List
        :list_data="list_data"
        @toggle-reminder="toggleReminder"
        @delete-item="deleteItem"
    />
</template>

<script>
import axios from "axios";
import config from "../api/config.json";

import Form from "../components/Form.vue";
import List from "../components/List.vue";

export default {
    components: { Form, List },
    props: {
        show_add_task_form: Boolean,
    },
    data() {
        return {
            list_data: [],
        };
    },
    methods: {
        async fetchData() {
            const { data } = await axios.get(config.apiEndpoint);
            return data;
        },
        async addItem(form_data) {
            await axios.post(config.apiEndpoint, form_data, {
                headers: { "Content-type": "application/json" },
            });
            this.list_data = await this.fetchData();
        },
        async deleteItem(id) {
            const url = `${config.apiEndpoint}/${id}`;
            if (confirm("确定要删除此条目？")) {
                await axios.delete(url);
            }
            this.list_data = await this.fetchData();
        },
        async toggleReminder(target_id) {
            const url = `${config.apiEndpoint}/${target_id}`;
            const { data: target } = await axios.get(url);
            await axios.put(url, { ...target, reminder: !target.reminder });
            this.list_data = await this.fetchData();
        },
    },
    async created() {
        this.list_data = await this.fetchData();
    },
};
</script>
