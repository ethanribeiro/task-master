<template>
    <form @submit.prevent="onSubmit">
        <h2 class="label-wrapper">
            <label for="new-task-input" class="label__lg">What needs to be done?</label>
        </h2>
        <input
            type="text"
            id="new-task-input"
            name="new-task"
            autocomplete="off"
            v-model.lazy.trim="label"
            class="input__lg" />
        <button type="submit" class="btn btn__primary btn__lg">Add</button>
    </form>
</template>

<script>
    export default {
        methods: {
            onSubmit() {
                // console.log(`Label value: ${this.label}`);
                if (this.label === "") {
                    return;
                }
                this.$emit("task-added", this.label);
                this.label = "";
            },
        },
        data() {
            return {
                label: "",
            };
        },
    };
</script>
