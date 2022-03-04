<template>
  <div class="nav_bar">
  </div>
  <div class="conteiner">
    <div class="maPage-tittle">
      <h3>Мои сайты:</h3>
      <my-button>
        + Добавить сайт
      </my-button>
    </div>
    <post-form @create = 'addPage'/>
    <page-list 
      :siteLists="siteLists"
      @remove = 'removePage'
      />
  </div>
</template>

<script>
import PageList from '@/components/PageList.vue'
import PostForm from '@/components/PageForm.vue'
export default {
  components:{
    PageList,
    PostForm,
  },
  data(){
    return {
      siteLists:[
        {id:1 , tittle: 'My page 1'},
        {id:2 , tittle: 'My page 2'},
        {id:3 , tittle: 'My page 3'},
        {id:4 , tittle: 'My page 4'},
      ],
    }
  },
  methods:{
    addPage(page) {
      this.siteLists.push(page)
      console.log(page)
    },
    removePage(page) {
      this.siteLists = this.siteLists.filter((item)=>item.id !== page.id)
    }
  }
}
</script>



<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.nav_bar{
  width: 100%;
  height: 50px;
  background-color: teal;
  margin-bottom: 20px;
}

.conteiner{
  margin: 0 50px;
}
.maPage-tittle{
  display: flex;
  justify-content: space-between;
  margin-bottom: 30px;
}

.page-list{
  display: flex;
  flex-wrap: wrap;
}

</style>