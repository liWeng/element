<template>
  <div style="margin: 20px;">
      <el-table
          ref="multipleTable"
          :data="tableData"
          tooltip-effect="dark"
          style="width: 100%"
          :highlight-selected-row="true"
          highlight-current-row
          @row-click="(row,column,event) => handleRowClick(row,column,event,'onclumn')"
          @selection-change="handleSelectionChange">
          <el-table-column
              type="selection"
              width="55">
          </el-table-column>
          <el-table-column
              label="日期"
              width="120">
              <template slot-scope="scope">{{ scope.row.date }}</template>
          </el-table-column>
          <el-table-column
              prop="name"
              label="姓名"
              width="120">
          </el-table-column>
          <el-table-column
              prop="address"
              label="地址"
              show-overflow-tooltip>
          </el-table-column>
      </el-table>
      <div style="margin-top: 20px">
          <el-button @click="toggleSelection([tableData[1], tableData[2]])">切换第二、第三行的选中状态</el-button>
          <el-button @click="toggleSelection()">取消选择</el-button>
      </div>
  </div>
</template>

<script>
  export default {
    data() {
        return {
            tableData: [{
                date: '2016-05-03',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-02',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-04',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-01',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-08',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-06',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-07',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }],
            multipleSelection: []
        }
    },

      methods: {
          toggleSelection(rows) {
              if (rows) {
                  rows.forEach(row => {
                      this.$refs.multipleTable.toggleRowSelection(row);
                  });
              } else {
                  this.$refs.multipleTable.clearSelection();
              }
          },
          handleRowClick(row,column,event, onclumn){
              var me = this;
              this.$refs.multipleTable.toggleRowSelection(row, row.flag);
          },
          handleSelectionChange(val) {
              this.multipleSelection = val;
          }
      }
  }
</script>
