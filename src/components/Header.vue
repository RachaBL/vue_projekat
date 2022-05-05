<template>
    <header>
        <h1>{{ title }}</h1>
        <Button @btn-click="$emit('toggle-add-task')" :text="showAddTask ? 'Zatvori' : 'Dodaj obavezu'" :color="showAddTask ? '#FF0000' : '#00FFAA'"/>
    </header>
</template>

<script>
import Button from './Button'

export default {
    name: 'Comp-Header',
    props: {
        title: String,
        showAddTask: Boolean
    },
    components: {
        Button
    }
}
</script>

<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>