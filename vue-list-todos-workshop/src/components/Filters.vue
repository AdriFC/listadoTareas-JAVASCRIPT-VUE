<template>
    <div>
        <button @click="changeFilter('all')">Todas</button>
        <button @click="changeFilter('incompleted')">Incompletas</button>
        <button @click="changeFilter('completed')">Completadas</button>
    </div>
</template>

<script>
export default {
    name: 'Filters',
    methods: {
        changeFilter(nameFilter){
            this.$emit('change-filter', nameFilter)
        }
    }
}
</script>


