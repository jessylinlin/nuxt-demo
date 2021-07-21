<template>
  <div id="app">
    <h2>{{ title }}</h2>
    <ul>
      <li
        v-for="item in posts"
        :key="item.id"
      >{{ item.title }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Home',
  components: {},
  //nuxt中的钩子函数 用于获取页面 服务端渲染 的数据
  async asyncData() {
    const { data } = await axios({
      method: 'GET',
      url: 'http://localhost:3000/data.json'
    })

    //这里返回的数据和data(){}中的数据合并 供页面使用
    // return {
    //   title: data.title,
    //   posts: data.posts
    // }
    return data
  }

  //vue中
  // data () {
  //   return {
  //     title: '',
  //     posts: []
  //   }
  // },
  // async created () {
  //   const { data } = await axios({
  //     method: 'GET',
  //     url: '/data.json'
  //   })
  //   this.title = data.title
  //   this.posts = data.posts
  // }
}
</script>

<style>
</style>
