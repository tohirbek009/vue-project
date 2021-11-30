<template>
    <button 
        :style="{background:color}" 
        class="btn"
        @click='onClick()'
    >{{ text }}</button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            color: String,
            text: String
        },
        methods: {
            onClick(){
                this.$emit("toggle-add-task")
            }
        }
    }
</script>
