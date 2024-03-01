<template>
  <el-table :data="list" style="width: 100%;padding-top: 15px;">
    <el-table-column label="在寻宠物名字(点击进入详情页)" width="300">
      <template slot-scope="scope">
        <a :href="`/pet-details/${scope.row.order_no}`" target="_blank" style="text-decoration: underline;"> 
        {{ "宠物名字" + scope.$index}}
        </a>
      </template>
    </el-table-column>
    <el-table-column label="丢失时间" width="195" align="center">
      <template slot-scope="scope">
        {{ scope.row.timestamp | parseTime('{y}-{m}-{d} {h}:{i}') }}
      </template>
    </el-table-column>
    <el-table-column label="丢失地点" min-width="195" align="center">
      <template slot-scope="scope">
        {{ "北京市海淀区XXX"}}
      </template>
    </el-table-column>
    <el-table-column label="宠物主人联系电话" width="195" align="center">
      <template slot-scope="scope">
        {{"185XXXXXXXX"}}
      </template>
    </el-table-column>
    <el-table-column label="宠物品种" width="195" align="center">
      <template slot-scope="scope">
        {{"哈士奇"}}
      </template>
    </el-table-column>
    <el-table-column label="状态" width="100" align="center">
      <template slot-scope="{row}">
        <el-tag :type="row.status | statusFilter">
          {{ row.status }}
        </el-tag>
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
import { transactionList } from '@/api/remote-search'

export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        已找回: 'success',
        找寻中: 'danger'
      }
      return statusMap[status]
    },
    orderNoFilter(str) {
      return str.substring(0, 30)
    }
  },
  data() {
    return {
      list: null
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      transactionList().then(response => {
        this.list = response.data.items.slice(0, 8)
      })
    }
  }
}
</script>
