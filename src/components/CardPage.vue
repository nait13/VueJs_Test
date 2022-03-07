<template>
    <div class="card">
        <h2>{{itemPage.tittle}}</h2>
        <hr>
        <div class="btn-section">
            <my-button @click="$emit('edit',itemPage)">Редактировать страницу</my-button>
            <my-button @click="$emit('remove',itemPage)">Удалить страницу</my-button>
            <my-button>Перейти на страницу</my-button>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        itemPage:{
            type:Object,
        }
    }
}
</script>

<style scoped>
.card{
  cursor: pointer;
  flex: 0 1 48%;
  padding: 20px;
  margin: 5px;
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.16);
}
.card:hover{
  box-shadow: 3px 6px 10px rgba(0, 0, 0, 0.16);
}
.card > h2{
  font-size: 2.0em;
  margin-bottom: 80px;
}
.card > hr {
  margin-bottom: 5px;
}
.btn-section{
  display: flex;
  justify-content: space-between;
}

</style>

