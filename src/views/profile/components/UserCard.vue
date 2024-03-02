<template>
  <el-card style="margin-bottom:20px;">
    <div slot="header" class="clearfix">
      <span>爱犬信息</span>
    </div>

    <div class="user-profile">
      <div class="box-center">
        <pan-thumb :image="user.avatar" :height="'100px'" :width="'100px'" :hoverable="false">
          <div>Hello</div>
          {{ user.role }}
        </pan-thumb>
      </div>
      <div class="box-center">
        <div class="user-name text-center">{{ user.name }}</div>
        <div class="user-role text-center text-muted">{{ user.role | uppercaseFirst }}</div>
      </div>
    </div>

    <div class="user-bio">
      <div class="user-education user-bio-section">
        <div class="user-bio-section-header"><svg-icon icon-class="education" /><span>主人信息</span></div>
          <div class="user-bio-section-body">  
    <table class="user-info-table">  
        <tbody>  
            <tr>  
                <th>用户ID:</th>  
                <td>123456</td>  
            </tr>  
            <tr>  
                <th>邮箱:</th>  
                <td>user@example.com</td>  
            </tr>  
            <tr>  
                <th>手机号:</th>  
                <td>+1234567890</td>  
            </tr>  
            <tr>  
                <th>创建时间:</th>  
                <td>2023-01-01 12:00:00</td>  
            </tr>  
            <tr>  
                <th>绑定的宠物ID:</th>  
                <td>123456789</td>  
            </tr>  
            <!-- 如果需要添加更多用户信息，可以继续添加行 -->  
        </tbody>  
        <tr>  
            <td colspan="2" style="text-align:center;">  
                <button type="button">更改</button>  
            </td>  
        </tr>
    </table>      
          </div> 
      </div>

      <!-- <div class="user-skills user-bio-section">
        <div class="user-bio-section-header"><svg-icon icon-class="skill" /><span>Skills</span></div>
        <div class="user-bio-section-body">
          <div class="progress-item">
            <span>Vue</span>
            <el-progress :percentage="70" />
          </div>
          <div class="progress-item">
            <span>JavaScript</span>
            <el-progress :percentage="18" />
          </div>
          <div class="progress-item">
            <span>Css</span>
            <el-progress :percentage="12" />
          </div>
          <div class="progress-item">
            <span>ESLint</span>
            <el-progress :percentage="100" status="success" />
          </div>
        </div>
      </div> -->
    </div>
  </el-card>
</template>

<script>
import PanThumb from '@/components/PanThumb'

export default {
  components: { PanThumb },
  props: {
    user: {
      type: Object,
      default: () => {
        return {
          name: '',
          email: '',
          avatar: '',
          role: ''
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.box-center {
  margin: 0 auto;
  display: table;
}

.text-muted {
  color: #777;
}

.user-profile {
  .user-name {
    font-weight: bold;
  }

  .box-center {
    padding-top: 10px;
  }

  .user-role {
    padding-top: 10px;
    font-weight: 400;
    font-size: 14px;
  }

  .box-social {
    padding-top: 30px;

    .el-table {
      border-top: 1px solid #dfe6ec;
    }
  }

  .user-follow {
    padding-top: 20px;
  }
}

.user-bio {
  margin-top: 20px;
  color: #606266;

  span {
    padding-left: 4px;
  }

  .user-bio-section {
    font-size: 14px;
    padding: 15px 0;

    .user-bio-section-header {
      border-bottom: 1px solid #dfe6ec;
      padding-bottom: 10px;
      margin-bottom: 10px;
      font-weight: bold;
    }
    .user-info-table {  
        width: 100%; /* 表格宽度占满容器 */  
        border-collapse: collapse; /* 合并相邻的边框 */  
        font-family: Arial, sans-serif; /* 设置字体 */  
        font-size: 14px; /* 设置字体大小 */  
    }  
  
    .user-info-table th,  
    .user-info-table td {  
        border: 1px solid #cccccc; /* 设置边框样式 */  
        padding: 10px; /* 设置内边距 */  
        text-align: left; /* 文本左对齐 */  
        vertical-align: top; /* 垂直对齐方式 */  
    }  
  
    .user-info-table th {  
        background-color: #e6e6e6; /* 设置表头背景色 */  
        color: #333333; /* 设置表头字体颜色 */  
    }  
  
    .user-info-table tr:nth-child(even) {  
        background-color: #f9f9f9; /* 设置偶数行背景色，实现条纹效果 */  
    }
  }  
}
</style>
