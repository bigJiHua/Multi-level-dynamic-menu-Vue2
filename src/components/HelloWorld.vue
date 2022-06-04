<template>
  <div class="hello">
    <button class="enbtn" @click="changelan">English/Chinese</button>
    <h2>{{enTitle}}</h2>
    <p>
      {{enTick}}
    </p>
    <router-link to="/Run">RUN</router-link>
  </div>
</template>

<script>
export default {
  data () {
    return {
      enTitle: '感谢你下载并试用Multi-level dynamic menu Vue2 的组件',
      enTick: `如果你在点击RUN后并没有看到什么，
      请检查你是否成功的安装并运行了json-server这个服务选项`
    }
  },
  name: 'HelloWorld',
  methods: {
    changelan () {
      this.toge = !this.toge
      if (this.toge) {
        this.enTitle = 'Thanks to download Multi-level dynamic menu Vue2 Module'
        this.enTick = `If you don't see anything after clicking run,
    Please check whether you have successfully installed and run the JSON server service option`
      } else {
        this.enTitle = '感谢你下载并试用Multi-level dynamic menu Vue2 的组件'
        this.enTick = `如果你在点击RUN后并没有看到什么，
      请检查你是否成功的安装并运行了json-server这个服务选项`
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
