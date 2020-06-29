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
      <!-- <div slot="slotItem">
        <el-table-column
          fixed="right"
          label="操作"
          align="center"
        >
          <template slot-scope="scope">
            <el-button
              type="text"
              size="small"
              @click="edit(scope.row.id)"
            >编辑</el-button>
            <el-button
              type="text"
              size="small"
              @click="del(scope.row.id)"
            >删除</el-button>
          </template>
        </el-table-column>
      </div> -->
    </my-table>
  </div>
</template>

<script>
import myTable from '../../components/table/table.vue'
export default {
  name: 'Dashboard',
  components: {
    myTable
  },
  data() {
    return {
      page: 1,
      total: 0,
      size: 10,
      tableColumns: [
        {
          type: 'text',
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'province', // <String>  对应属性名
          label: '省', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          type: 'text',
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          prop: 'city', // <String>  对应属性名
          label: '市', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          type: 'text',
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          isBtn: false, // <Boolean> 是否排序
          prop: 'district', // <String>  对应属性名
          label: '区', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          type: 'img',
          hasSort: false, // <Boolean> 是否排序
          isShow: true, // <Boolean> 是否展示
          isBtn: false, // <Boolean> 是否排序
          prop: 'banner', // <String>  对应属性名
          label: '轮播图', // <String>   表头标签
          textalgin: 'center' // <String>   表格内容对齐方式
        },
        {
          type: 'btn',
          isShow: true, // <Boolean> 是否展示
          prop: 'operate', // <String>  对应属性名
          label: '操作', // <String>   表头标签
          textalgin: 'center', // <String>   表格内容对齐方式
          operates: [{
            type: 'primary',
            size: 'small',
            label: '编辑',
            method: (row, index) => {
              this.handleEdit(row, index)
            }
          }, {
            type: 'danger',
            size: 'small',
            label: '删除',
            method: (row, index) => {
              this.handleRemove(row, index)
            }
          }]
        }
      ],
      tableData: [{
        province: '浙江省',
        city: '杭州市',
        district: '江干区',
        banner: 'https://lhcp2020.oss-cn-beijing.aliyuncs.com/20200429/图层 172.png'
      }]
    }
  },
  methods: {
    pageChange(val) {
      console.log(val)
    },
    handleEdit(row, index) {
      console.log(row)
    },
    handleRemove(row, index) {
      console.log(row)
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
