<template>
  <div class="app-container">
    <el-form
      ref="valueFrom"
      :model="form"
      label-width="100px"
      :rules="rules"
    >
      <el-form-item
        label="名字："
        prop="name"
      >
        <el-input
          v-model="form.name"
          class="formInput"
          placeholder="请输入名字"
        />
      </el-form-item>
      <el-form-item
        label="性别"
        prop="sex"
      >
        <el-select
          v-model="form.sex"
          placeholder="请选择你的性别"
        >
          <el-option
            v-for="item in selectOption"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          />
        </el-select>
      </el-form-item>
      <el-form-item>
        <el-button
          type="primary"
          @click="onSubmit('valueFrom')"
        >确定</el-button>
        <el-button @click="onCancel">返回</el-button>
        <el-button @click="resetForm('valueFrom')">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        sex: ''
      },
      rules: {
        name: [{ required: true, message: '请输入活动名称', trigger: 'blur' }],
        sex: [{ required: true, message: '请选择性别', trigger: 'blur' }]
      },
      selectOption: [
        {
          label: '男',
          value: '1'
        },
        {
          label: '女',
          value: '2'
        }
      ]
    }
  },
  methods: {
    onSubmit(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          console.log(valid)
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    onCancel() {
      this.$message({
        message: 'cancel!',
        type: 'warning'
      })
    },
    resetForm(formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<style scoped>
.line {
  text-align: center;
}
</style>

