<template>
    
        
    <div class="md-layout md-gutter">
      <div class="md-layout-item md-size-25"></div>
      <div class="md-layout-item md-size-50">
        <md-button @click="changeFilter('all')" class="md-primary">Todas</md-button>        
        <md-button @click="changeFilter('incompleted')" class="md-primary">Incompletas</md-button>       
        <md-button @click="changeFilter('completed')" class="md-primary">Completadas</md-button>
      </div>
      <div class="md-layout-item md-size-25"></div>
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


