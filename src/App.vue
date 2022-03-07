<template>
  <div class="nav_bar">
  </div>
  <div class="conteiner">
    <div class="maPage-tittle">
      <h3>Мои сайты:</h3>
      <my-button @click = 'showModal'>
        + Добавить сайт
      </my-button>
    </div>
    <my-modal v-model:show = 'modalVisible'>
      <post-form :edit="editTitle" @create = 'addPage'/>
    </my-modal>
    <page-list 
      :siteLists="siteLists"
      @remove = 'removePage'
      @edit = 'editPage'
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
      modalVisible:false,
      editing: false,
      editTitle:'',

    }
  },
  methods:{
    addPage(page) {
      this.siteLists.push(page)
      this.modalVisible = false
    },
    removePage(page) {
      this.siteLists = this.siteLists.filter((item)=>item.id !== page.id)
    },
    showModal(){
      this.modalVisible = true;

    },
    editPage(page){
      let findPage = this.siteLists.find((item) => item.id === page.id)
      console.log(findPage.tittle)
      this.editTitle = findPage.tittle
      this.modalVisible = true

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