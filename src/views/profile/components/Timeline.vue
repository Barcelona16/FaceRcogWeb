<template>
  <div class="block">
    <el-timeline>
      <el-timeline-item v-for="(item,index) of timeline" :key="index" :timestamp="item.timestamp" placement="top">
        <el-card>
          <h4>{{ item.title }}</h4>
          <p>{{ item.content }}</p>
        </el-card>
      </el-timeline-item>
    </el-timeline>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timeline: [
        {
          timestamp: '2021/3/12',
          title: '第一次注册',
          content: '2021-03-12 15:40:23'
        },
        {
          timestamp: '2021/4/21',
          title: '第一次信息登记',
          content: '爱犬旺财已与您的账户绑定！'
        },
        {
          timestamp: '2022/3/10',
          title: '爱犬一岁啦',
          content: '旺财生日快乐！'
        },
        {
          timestamp: '2023/4/23',
          title: '疫苗信息登记成功',
          content: '您已为爱犬成功登记疫苗信息！'
        }
      ]
    }
  }
}
</script>
