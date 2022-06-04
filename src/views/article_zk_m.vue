<template>
  <div class="listM">
    <p class="montitle"  @click="mdod()">{{ art }}</p>
    <ol
      v-for="(obj, index) in newList[index]" :key="index" class="list_ui"
      :class="{ mlists: misOpen, mlist: !misOpen }">
      <li class="list_li">
        <a :href="obj.hurl">
          {{ obj.title }}
        </a>
      </li>
    </ol>
  </div>
</template>

<script>
// 导入组件
// import  from ''

export default {
  props: {
    index: {
      type: Number,
      default: -1
    },
    art: {
      type: String,
      default: ''
    },
    newList: {
      type: Array
    }
  },
  data () {
    return {
      misOpen: false
    }
  },
  methods: {
    mdod () {
      this.misOpen = !this.misOpen
    }
  },
  name: 'articleListZk',
  components: {
    // 导入组件
  }
}
</script>

<style lang="less" scoped>
.montitle{
  font-size: 1.2rem;
  margin: 0;
}
.list_ul{
  list-style: none;
}
.mlist{
  display: none;
}
.mlists{
  display: block;
}
.list_li{
  a{
    text-decoration: none;
    color: white;
  }
  a:hover{
    color: rgba(0,0,0,0.8);
  }
}
</style>
