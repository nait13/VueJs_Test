<template>
    <form @submit.prevent>
        Tittle name:
        <my-input 
          type="text" 
          placeholder="name"
          v-model="page.tittle"
        />
        <my-button @click='createPage'>OK</my-button>
    </form>
</template>

<script>
export default {
    props:{
        edit:{
            type:Object,
        }
    },
    data(){
        return {
            page:{
                tittle:'',
            }
        }
    },
    methods:{
        createPage(){
            if(this.page.tittle.trim() === '' ) return
            this.page.id = Date.now()
            this.$emit('create',this.page)
            this.page = {
                tittle: '',
            }
        }
    }
}
</script>

<style scoped>

</style>