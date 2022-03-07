<template>
  <h3>Список сайтов:</h3>
  <div class="page-list">
      <card-page
        v-for="page in siteLists"
        :key="page.id"
        :itemPage="page"
        @edit = "$emit('edit',page)"
        @remove = "$emit('remove', page)"
      />
  </div>
</template>

<script>
import CardPage from '@/components/CardPage.vue'
export default {
    components:{
        CardPage,
    },
    props:{
        siteLists:{
            type:Array,
        }
    }
}
</script>

<style>
.page-list{
  display: flex;
  flex-wrap: wrap;
}
</style>