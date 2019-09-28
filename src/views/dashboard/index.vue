<template>
  <div class="app-container">
     <my-table
       :columns="tableColumns"
       :data-source="tableData"
       :text-align="`center`"
       :header-align="'center'"
       :show-pagination="true"
       :page="page"
       :size="size"
       :total="total"
       @pageChange="pageChange"
     >
       <div slot="slotItem">
         <el-table-column fixed="right" label="操作" align="center">
           <template slot-scope="scope">
             <el-button type="text" size="small" @click="edit(scope.row.id)">编辑</el-button>
             <el-button v-if="identity=='admin'" type="text" size="small" @click="del(scope.row.id)">删除</el-button>
           </template>
         </el-table-column>
       </div>
     </my-table>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import myTable from '../../components/table/table.vue'
export default {
  name: 'Dashboard',
  components:{
    myTable
  },
  data(){
    return{
      page:1,
      total:0,
      size:10,
      tableColumns: [
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'province', // <String>  对应属性名
          label: '省', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'city', // <String>  对应属性名
          label: '市', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'district', // <String>  对应属性名
          label: '区', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'campus', // <String>  对应属性名
          label: '校区', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'principal', // <String>  对应属性名
          label: '校长', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'mobile', // <String>  对应属性名
          label: '客服电话', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'username', // <String>  对应属性名
          label: '账号', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'password', // <String>  对应属性名
          label: '密码', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'principalCode', // <String>  对应属性名
          label: '校长码', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'teacherCode', // <String>  对应属性名
          label: '教师码', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'studentCode', // <String>  对应属性名
          label: '学生码', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        }
      ],
      tableData: [],
    }
  },
  methods:{
    pageChange(val){
      console.log(val)
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
