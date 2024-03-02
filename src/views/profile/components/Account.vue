<template>  
  <el-form :model="formData" label-width="120px">  
    <el-row :gutter="20">  
      <el-col :span="12">    
        <el-form-item label="宠物名字">  
          <el-input v-model.trim="formData.pet.name" />  
        </el-form-item>  
        <el-form-item label="品种">  
          <el-input v-model.trim="formData.pet.breed" />  
        </el-form-item>  
        <el-form-item label="颜色">  
          <el-input v-model.trim="formData.pet.color" />  
        </el-form-item>  
        <el-form-item label="年龄">  
          <el-input-number v-model.number="formData.pet.age" :min="0" />  
        </el-form-item>  
        <el-form-item label="性别">  
          <el-select v-model="formData.pet.gender">  
            <el-option label="公" value="male" />  
            <el-option label="母" value="female" />  
          </el-select>  
        </el-form-item>  
        <el-form-item label="生日">  
          <el-date-picker v-model="formData.pet.birthday" type="date" placeholder="选择日期" />  
        </el-form-item>  
        <el-form-item label="体重">  
          <el-input-number v-model.number="formData.pet.weight" :min="0" label="kg" />  
        </el-form-item>  
      </el-col>  
      <el-col :span="12">  
        <el-form-item label="宠物ID">  
          <span>{{ formData.pet.id }}</span>  
        </el-form-item>  
        <el-form-item label="宠物图片">  
          <el-upload  
            action="your-upload-url"  
            :on-success="handleUploadSuccess"  
            :before-upload="beforePetImageUpload"  
            :show-file-list="false"  
          >  
            <el-button slot="trigger" size="small" type="primary">选择图片</el-button>  
          </el-upload>  
        </el-form-item>  
        <el-form-item label="保险情况">  
          <el-switch v-model="formData.pet.hasInsurance" active-color="#13ce66" inactive-color="#ff4949" />  
        </el-form-item>  
        <el-form-item label="是否已打疫苗">  
          <el-switch v-model="formData.pet.isVaccinated" active-color="#13ce66" inactive-color="#ff4949" />  
        </el-form-item>  
        <el-form-item label="是否已驱虫">  
          <el-switch v-model="formData.pet.isDewormed" active-color="#13ce66" inactive-color="#ff4949" />  
        </el-form-item>  
        <el-form-item label="更新时间">  
          <span>{{ formattedUpdateTime }}</span>  
        </el-form-item>  
      </el-col>  
    </el-row>  
  
    <el-form-item>  
      <el-button type="primary" @click="submit">Update</el-button>  
    </el-form-item>  
  </el-form>  
</template>  
  
<script>  
export default {  
  data() {  
    return {  
      formData: {  
        user: {  
          name: '',  
          email: ''  
        },  
        pet: {  
          id: '123456789',  
          name: '',  
          breed: '',  
          color: '',  
          age: 0,  
          gender: '',  
          birthday: '',  
          weight: 0,  
          hasInsurance: false,  
          isVaccinated: false,  
          isDewormed: false,  
          updatedAt: new Date().toISOString()  
        }  
      }  
    };  
  },  
  computed: {  
    formattedUpdateTime() {  
      return this.formData.pet.updatedAt.toLocaleString();  
    }  
  },  
  methods: {  
    submit() {  
      this.$message({  
        message: 'User information has been updated successfully',  
        type: 'success',  
        duration: 5000  
      });  
    },  
    handleUploadSuccess(response, file, fileList) {  
      console.log('Upload success:', response);  
    },  
    beforePetImageUpload(file) {  
      const isJPG = file.type === 'image/jpeg' || file.type === 'image/png';  
      const isLt2M = file.size / 1024 / 1024 < 2;  
  
      if (!isJPG) {  
        this.$message.error('Upload JPG/PNG images only!');  
      }  
      if (!isLt2M) {  
        this.$message.error('Image size cannot exceed 2MB!');  
      }  
  
      return isJPG && isLt2M;  
    }  
  }  
};  
</script>