<template>
  <div class="app-container">
    <h1>{{ "ID：28763 犬识别结果" }} </h1>
    <div class="table-with-description">  
    <el-table v-loading="listLoading" :data="list" border fit highlight-current-row style="width: 70%">
      <el-table-column align="center" label="ID" width="80px">
        <template slot-scope="scope">
          <span>{{ scope.row.id }}</span>
        </template>
      </el-table-column>

      <el-table-column width="280px" align="center" label="最近更新时间">
        <template slot-scope="scope">
          <span>{{ scope.row.timestamp }}</span>
        </template>
      </el-table-column>

      <el-table-column width="150px" align="center" label="登记人">
        <template slot-scope="scope">
          <span>{{ scope.row.author }}</span>
        </template>
      </el-table-column>

      <el-table-column width="150px" label="相似度">
        <template slot-scope="scope">
          <svg-icon v-for="n in +scope.row.importance" :key="n" icon-class="star" class="meta-item__icon" />
        </template>
      </el-table-column>

      <el-table-column class-name="status-col" label="犬状态">
        <template slot-scope="{row}">
          <el-tag :type="row.status | statusFilter">
            {{ row.status }}
          </el-tag>
        </template>
      </el-table-column>

      <!-- <el-table-column min-width="300px" label="犬">
        <template slot-scope="{row}">
          <router-link :to="'/example/edit/'+row.id" class="link-type">
            <span>{{ row.title }}</span>
          </router-link>
        </template>
      </el-table-column> -->

      <el-table-column align="center" label="点击查看" width="200">
        <template slot-scope="scope">
          <router-link :to="'/example/edit/'+scope.row.id">
            <el-button type="primary" size="small" icon="el-icon-click">
              点击查看
            </el-button>
          </router-link>
        </template>
      </el-table-column>
    </el-table>
    <div class="table-description">  
  <p class="description-header">识别结果说明：</p>  
  <ul class="description-list">  
    <li class="description-item">  
      <strong>第一档⭐⭐⭐：</strong> 很有可能为同一只犬。  
    </li>  
    <li class="description-item">  
      <strong>第二档⭐⭐：</strong> 可能是同一只犬，但是有部份特征不同。  
    </li>  
    <li class="description-item">  
      <strong>第三档⭐：</strong> 同一只犬可能性较小，建议上传爱犬其他图片再次尝试。  
    </li>  
  </ul>  
</div>
    </div>  

    <pagination v-show="total>0" :total="total" :page.sync="listQuery.page" :limit.sync="listQuery.limit" @pagination="getList" />
  </div>
</template>

<script>
import { fetchList } from '@/api/article'
import Pagination from '@/components/Pagination' // Secondary package based on el-pagination

export default {
  name: 'ArticleList',
  components: { Pagination },
  filters: {
    statusFilter(status) {
      const statusMap = {
        活跃: 'success',
        已过期: 'info',
        已寻回: 'danger'
      }
      return statusMap[status]
    }
  },
  data() {
    return {
      list: null,
      total: 0,
      listLoading: true,
      listQuery: {
        page: 1,
        limit: 20
      }
    }
  },
  created() {
    this.getList()
  },
  methods: {
    getList() {
      this.listLoading = true
      fetchList(this.listQuery).then(response => {
        this.list = response.data.items
        this.total = response.data.total
        this.listLoading = false
      })
    }
  }
}
</script>

<style scoped>
.edit-input {
  padding-right: 100px;
}
.cancel-btn {
  position: absolute;
  right: 15px;
  top: 10px;
}

  
.table-with-description .el-table {  
  /* 表格已经有一个内联样式设置了宽度，这里不需要额外设置 */  
}  
  
.table-with-description .table-description {  
  flex-grow: 1; /* 使描述占据剩余空间 */  
  margin-left: 20px; /* 在表格和描述之间添加间距 */  
}  

.table-description {  
  margin-left: 20px; /* 根据需要调整上边距 */  
  font-size: 16px; /* 文本大小 */  
  line-height: 1.5; /* 行高 */  
}  
  
.description-header {  
  font-weight: bold; /* 加粗标题文本 */  
  margin-bottom: 15px; /* 标题与列表之间的间距 */  
}  
  
.description-list {  
  list-style-type: none; /* 移除默认的列表标记 */  
  padding-left: 0; /* 移除默认的列表缩进 */  
}  
  
.description-item {  
  margin-bottom: 5px; /* 列表项之间的间距 */  
}  
  
.description-item strong {  
  display: inline-block; /* 使强调文本块级显示 */  
  width: 200px; /* 设置固定宽度，使列表对齐 */  
}
</style>
