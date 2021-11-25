<template>
    <div class="container">
        <Header @show-add-task-form="showAddTaskForm" :title="header_text" />
        <router-view :show_add_task_form="show_add_task_form"></router-view>
        <Footer />
    </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
export default {
    name: "App",
    components: { Header, Footer },
    data() {
        return {
            header_text: "Todo List",
            show_add_task_form: false,
        };
    },
    methods: {
        showAddTaskForm() {
            this.show_add_task_form = !this.show_add_task_form;
        },
    },
};
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
body {
    font-family: "Poppins", sans-serif;
}
.container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
}
.btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
}
</style>
