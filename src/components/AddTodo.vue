<template>
    <form
        @submit.prevent="addTodo"
    >
        <input
            type="text"
            placeholder="Add todo..."
            v-model='todo'
        />
        <input
            type='submit'
            value='Add Todo'
        />
    </form>
</template>

<script lang='ts'>
    export default {
        name: 'AddTodo',
        data() {
            return {
                todo: ''
            }
        },
        methods: {
            addTodo(e: Event){
                if(!this.todo) {
                    alert("Todo cannot be empty");
                    return;
                }

                this.$emit(`addTodo`, this.todo, () => {
                    this.todo = '';
                });
            }
        }
    }
</script>

<style>

</style>
