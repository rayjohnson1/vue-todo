<template>
    <figure 
          class='todo-item'
    >
        <i v-if="todo.completed" class="fas fa-check-circle todo-item__status todo-item__status--complete"></i>
        <i v-else class="far fa-check-circle todo-item__status todo-item__status--incomplete"></i>
        <div>
            <h5>{{ todo.title }}</h5>
            <p v-if="todo.description">{{ todo.description }}</p>
        </div>
        <div>
            <button 
                @click="$emit('completeItem', todo.id)"
                v-if='!todo.completed'
            >Complete</button>
            <button 
                @click="$emit('markIncomplete', todo.id)"
                v-else
            >Mark Incomplete</button>
            <button
                @click='$emit("deleteItem", todo.id)'
            >Delete</button>
        </div>
    </figure>
</template>

<script>
export default {
    name:'TodoItem',
    props: ['todo']
}
</script>

<style scoped lang='scss'>
.todo-item{
    margin-bottom: 5rem;
    display: grid;
    grid-gap: 1rem;
    background: white;
    box-shadow: 0 1rem 2rem rgba(black, .1);
    padding: 2rem;
}
</style>
