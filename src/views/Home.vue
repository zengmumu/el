<template>
  <div class="home">
  <h1>首页</h1>
  <el-button type="primary" icon="el-icon-circle-plus-outline" @click="showAdd.show=true">添加</el-button>
  <el-table
    :data="tableData"
    stripe
    style="width: 100%">
    <el-table-column
      prop="date"
      label="日期"
      width="180">
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      width="180">
    </el-table-column>
    <el-table-column
      prop="address"
      label="地址">
    </el-table-column>
    <el-table-column      
      label="操作">
      <template slot-scope="scope">
        <el-button
          size="mini"
          @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)">删除</el-button>
      </template>
    </el-table-column>
  </el-table>
  <user-add :showAdd="showAdd" @eventadd=handleAdd($event)></user-add>
  <user-edit :showEdit="showEdit" :pform="pform"></user-edit>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import UserAdd from '@/components/UserAdd'
import UserEdit from '@/components/UserEdit'
export default {
  name: 'home',
  methods:{
    handleAdd(event){
      this.tableData.unshift(event);
    },
    handleEdit(index,row){
      this.showEdit.show = true;
      this.pform = row;
      console.log(index,row)
    },
    handleDelete(index,row){
      console.log(index,row)
      let flag = window.confirm("你确定要删除吗？")
      if(flag){
        let ind = this.tableData.indexOf(row);
        this.tableData.splice(ind,1);
      }

    },
  },
  components: {    
    UserAdd,UserEdit
  },
   data() {
      return {
        pform:{},
        showEdit:{show:false},
        showAdd:{show:false},
        tableData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄'
        }]
      }
    }

}
</script>
