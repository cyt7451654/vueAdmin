
<template>
  <div class="components">
    <el-table
      border
      :data="dataSource"
      @selection-change="handleSelectionChange"
    >
      <!--选择-->
      <el-table-column
        v-if="hasSelection"
        type="selection"
        width="55"
        :align="textAlign"
      />
      <!--序号-->
      <el-table-column
        v-if="hasIndex"
        type="index"
        width="55"
        :align="textAlign"
      />
      <!--数据源-->
      <el-table-column
        v-for="column in columns"
        v-show="column.isShow"
        :key="column.prop"
        :header-align="headerAlign"
        :sortable="column.hasSort"
        :prop="column.prop"
        :label="column.label"
        :align="textAlign"
        :width="column.width"
        :fixed="column.fixed"
      >
        <template slot-scope="scope">
          <template v-if="column.type=='btn'">
            <el-button
              v-for="(btn,index) in column.operates"
              :key="index"
              :type="btn.type"
              :size="btn.small"
              @click.native.prevent="btn.method(scope.row, scope.$index)"
            >{{ btn.label }}</el-button>
          </template>
          <template v-if="column.type=='text'">
            {{ scope.row[column.prop] }}
          </template>
          <template v-if="column.type=='img'">
            <img
              :src="scope.row[column.prop]"
              class="tableImg"
            >
          </template>
        </template>
      </el-table-column>
      <!--操作-->
      <slot name="slotItem" />
    </el-table>
    <div class="pagination">
      <el-pagination
        v-if="showPagination==true"
        :page-size="size"
        :current-page="page"
        :total="total"
        background
        layout="prev, pager, next, jumper"
        @current-change="pageChange"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'TmTable',
  props: {
    // 表头对齐方式
    headerAlign: {
      type: String,
      default: 'left'
    },
    // 表内容对齐方式
    textAlign: {
      type: String,
      default: 'left'
    },
    // 是否可以选择
    hasSelection: {
      type: Boolean,
      default: function () {
        return false
      }
    },
    // 是否有序列项
    hasIndex: {
      type: Boolean,
      default: function () {
        return false
      }
    },
    // 这是相应的字段展示
    columns: {
      type: Array,
      default: function () {
        return []
      }
    },
    // 这是数据源
    dataSource: {
      type: Array,
      default: function () {
        return []
      }
    },
    showPagination: {
      type: Boolean,
      default: false
    },
    // 分页相关数据
    page: {
      type: Number,
      default: 1
    },
    size: {
      type: Number,
      default: 10
    },
    total: {
      type: Number,
      default: 0
    }
  },
  methods: {
    // 将选中的行发送到父组件
    handleSelectionChange(val) {
      const selectionArr = []
      val.forEach(function (el) {
        selectionArr.push(el)
      })
      this.$emit('commitSelection', selectionArr)
    },
    pageChange(val) {
      this.$emit('pageChange', val)
    }
  }
}
</script>

<style scoped>
.pagination {
  margin-top: 30px;
  text-align: right;
}
</style>
