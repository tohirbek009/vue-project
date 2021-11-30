<template>
    <header>
        <p>{{ title }}</p>
        <Button @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add'" :color="showAddTask ? 'crimson':'green'"/>
    </header>
</template>
 
<script>
import Button from './Button.vue'
    export default {
        name: 'Header',
        props: {
            title: String,
            showAddTask: Boolean
        },
        components: {
            Button
        }
    }
</script>

<style>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>