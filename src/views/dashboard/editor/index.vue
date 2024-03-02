<template>
  <div class="dashboard-editor-container">
    <div class=" clearfix">
      <pan-thumb :image="avatar" style="float: left">
        Your roles:
        <span v-for="item in roles" :key="item" class="pan-info-roles">{{ item }}</span>
      </pan-thumb>
      <github-corner style="position: absolute; top: 0px; border: 0; right: 0;" />
      <div class="info-container">
        <span class="display_name">{{ "普通用户" }}</span>
        <span style="font-size:20px;padding-top:20px;display:inline-block;">旺财's 信息卡</span>
      </div>
    </div>
    <div>

      <img :src="emptyGif" class="emptyGif" style="float: left">
      <table class="dog-info-table">    
  <tr>    
    <th>基本信息</th>    
    <th>详情</th>    
    <th>健康信息</th>    
    <th>详情</th>    
  </tr>    
  <tr>    
    <td>姓名</td>    
    <td>旺财</td>    
    <td>疫苗</td>    
    <td>已打</td>    
  </tr>    
  <tr>    
    <td>年龄</td>    
    <td>3岁</td>    
    <td>驱虫</td>    
    <td>每月一次</td>    
  </tr>    
  <tr>    
    <td>性别</td>    
    <td>公</td>    
    <td>体检</td>    
    <td>每年一次</td>    
  </tr>    
  <tr>    
    <td>品种</td>    
    <td>萨摩耶</td>    
    <td>保险</td>    
    <td>XXX</td>    
  </tr>  
  <tr>    
    <td>生日</td>    
    <td>2021-01-01</td>    
    <td>绝育</td>    
    <td>已完成</td>    
  </tr>    
  <tr>    
    <td>体重</td>    
    <td>20kg</td>    
    <td>更新时间</td>    
    <td>2024-01-02</td>    
  </tr>    
  <!-- 其他信息可以继续添加 -->  
</table>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import PanThumb from '@/components/PanThumb'
import GithubCorner from '@/components/GithubCorner'

export default {
  name: '普通用户',
  components: { PanThumb },
  data() {
    return {
      // emptyGif: 'https://wpimg.wallstcn.com/0e03b7da-db9e-4819-ba10-9016ddfdaed3'
      emptyGif: require('@/assets/avatar/dog1.jpg') // 使用 require 引入本地图片
    }
  },
  computed: {
    ...mapGetters([
      'name',
      'avatar',
      'roles'
    ])
  }
}
</script>

<style lang="scss" scoped>
  .emptyGif {
    display: block;
    padding:50px 60px 0px;
    width: 30%;
    margin: 0;
  }
  .dog-info-table {  
      //padding:50px 60px 0px; // 表格与图片之间的间距  
      border-collapse: collapse; // 合并边框  
      display: block;
      padding:50px 400px 100px;
      //width: 30%;
      //margin: 0;
      th, td {  
      border: 1px solid #ddd; // 边框样式  
      padding: 8px; // 内边距  
      text-align: left; // 文字左对齐  
    }  
  
    th {  
      background-color: #f2f2f2; // 表头背景色  
      font-weight: bold; // 表头字体加粗  
    }  
  }  

  .dashboard-editor-container {
    background-color: #e3e3e3;
    min-height: 100vh;
    padding: 50px 60px 0px;
    .pan-info-roles {
      font-size: 12px;
      font-weight: 700;
      color: #333;
      display: block;
    }
    .info-container {
      position: relative;
      margin-left: 190px;
      height: 150px;
      line-height: 200px;
      .display_name {
        font-size: 48px;
        line-height: 48px;
        color: #212121;
        position: absolute;
        top: 25px;
      }
    }
  }
</style>
