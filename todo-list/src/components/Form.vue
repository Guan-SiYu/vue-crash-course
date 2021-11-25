<template>
    <div v-show="show_add_task_form">
        <form action="" @submit="handleSubmit">
            <div class="form-control">
                <label for="info">你的下一下一项计划 ✏️</label>
                <input
                    v-model="info"
                    type="text"
                    id="info"
                    placeholder="your task thing"
                />
            </div>
            <div class="form-control">
                <label for="day">⏱ 日期 & 时间</label>
                <input
                    v-model="day"
                    type="text"
                    id="day"
                    placeholder="When do you want do"
                />
            </div>
            <div class="form-control form-control-check">
                <label for="reminder">⏰ 设置提醒</label>
                <input
                    v-model="reminder"
                    type="checkbox"
                    id="reminder"
                    name="reminder"
                />
            </div>
            <input type="submit" value="Submit" class="btn btn-block" />
        </form>
    </div>
</template>
<script>
export default {
    props: {
        show_add_task_form: Boolean,
    },
    data() {
        return {
            info: "",
            day: "",
            reminder: "",
        };
    },
    methods: {
        handleSubmit(e) {
            e.preventDefault();
            if (!this.info) return alert("Please add a task");
            const form_data = {
                info: this.info,
                day: this.day,
                reminder: this.reminder,
            };
            this.$emit("add-item", form_data);
        },
    },
};
</script>
<style scoped>
.add-form {
    margin-bottom: 40px;
}
.form-control {
    margin: 20px 0;
}
.form-control label {
    display: block;
}
.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}
.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.form-control-check label {
    flex: 1;
}
.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>
