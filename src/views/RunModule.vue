<template>
  <div class="RunView">
    <button class="enbtn" @click="changelan">English/Chinese</button>
    <header class="ararc_title">{{enTitle}}</header>
    <div class="ararc_list">
      <span class="list_year" @click.prevent="listod()">{{enYear}}</span>
      <div :class="{ list_down: isOpen,'list_open': !isOpen }" id="new_article_list_m">
        <div class="month" v-for="(art, index) in monthlist" :key="index">
          <Articlezkm
          :index=index
          :newList="newList"
          :art="art"
          ></Articlezkm>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Articlezkm from './article_zk_m.vue'

export default {
  props: [],
  data () {
    return {
      newList: [],
      monthlist: [],
      isOpen: true,
      enTitle: '文章归档',
      enYear: '2021年',
      toge: false
    }
  },
  // 生命周期初始化函数
  created () {
    this.getdata()
  },
  // 方法
  methods: {
    listod () {
      this.isOpen = !this.isOpen
    },
    async getdata () {
      //                                    may change here ↓
      // const { data: res } = await axios.get('http://localhost:3000/data')
      const { data: res } = await axios.get('http://api.da4.cc/uploads/data.json')
      const newres = res.data // 因为这个接口返回的并不是一个数组
      const articleList = [...new Set(newres.map((word) => word.month))]
      const newalist = []
      for (let i = 0; i < articleList.length; i++) {
        const newarr = newres.filter((word) => word.month === articleList[i])
        newalist.push(newarr)
      }
      this.monthlist = articleList
      this.newList = newalist
    },
    changelan () {
      this.toge = !this.toge
      if (this.toge) {
        this.enTitle = 'Article archiving'
        this.enYear = '2021'
      } else {
        this.enTitle = '文章归档'
        this.enYear = '2021 年'
      }
    }
  },
  name: 'ArtListModule',
  components: {
    Articlezkm
    // 导入组件
  }
}
</script>

<style lang="less" scoped>
*{
  margin: 0;
  padding: 0;
}
.RunView{
  width: 75vw;
  margin: 10vh auto;
  header{
    text-align: center;
    font-size: 2rem;
    font-weight: bolder;
    font-family: 'songti';
  }
}
.list_year {
  font-size: 2rem;
  font-weight: 600;
  font-style: oblique;
  color: rgb(34, 32, 30);
}
.ararc_list {
  margin-top: 10px;
  background-color: rgba(173, 207, 235, 0.6);
  border-radius: 11px;
  padding: 10px;
  opacity: 0.9;
}
.list_down {
  display: none;
}
.list_open {
  font-weight: 500;
}
.listM{
  text-align: left;
  font-weight: bolder;
  margin: 0;
  padding: 0;
  background-color: rgba(90, 160, 218, 0.6);
  padding: 5px;
  border-radius: 5px;
  margin-bottom: 15px;
}
.listM:hover{
  background-color: rgba(97, 170, 229, 0.873);
}
</style>
