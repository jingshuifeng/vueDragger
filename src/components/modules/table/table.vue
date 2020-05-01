<template>
  <div class="table">
      <button @click="showEdit">新增</button>
      <component :is="editTableItem" @submitss="handleClickAdd"
      @submitEsc="handleClickAdd" :tableItem="tableItem" :index="index" :readonly="readonly" :isEdit="isEdit"></component>
      
      <el-table
    :data="tableData"
    border
    style="width: 100%">
    <el-table-column
      fixed
      prop="date"
      label="日期"
      width="150">
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      width="120">
    </el-table-column>
    <el-table-column
      prop="province"
      label="省份"
      width="120">
    </el-table-column>
    <el-table-column
      prop="city"
      label="市区"
      width="120">
    </el-table-column>
    <el-table-column
      prop="address"
      label="地址"
      width="300">
    </el-table-column>
    <el-table-column
      prop="zip"
      label="邮编"
      width="120">
    </el-table-column>
    <el-table-column
      fixed="right"
      label="操作"
      >
      <template slot-scope="scope">
        <el-button @click="handleClickRead(scope.row)" type="text" size="small">查看</el-button>
        <el-button type="text" size="small" @click="handleClickEdit(scope.row,scope.$index)">编辑</el-button>
        <el-button type="text" size="small" @click="handleClickDelete(scope.$index)">删除</el-button>
      </template>
    </el-table-column>
  </el-table>
  </div>
</template>

<script>
import editTableItem from './editTableItem'
  export default {
    components:{
      editTableItem
    },
    methods: {
      handleClickRead(row) {
        this.readonly=true
        row.date=new Date(row.date)
        this.tableItem=row
        this.editTableItem='editTableItem'
      },
      handleClickEdit(row,index) {
        this.readonly=false
        row.date=new Date(row.date)
        this.tableItem=row
        this.editTableItem='editTableItem'
        this.index=index
        this.isEdit=true
      },
      handleClickDelete(index) {
          this.tableData.splice(index,1)
        
      },
      showEdit(){
        this.readonly=false
        this.tableItem={}
        this.editTableItem='editTableItem'
      },
      handleClickAdd(e) {
        console.log(e)
        this.tableData[e.index]=e.sizeForm
        if(e.sizeForm){
          this.tableData.push(e.sizeForm)
        }
        this.editTableItem=e.editTableItem
        
      }
    },
    created(){
      this.index=this.tableItem.length+1
    },
    props:{
        tableDataProp:{
            type:Array
        }
    },
    data() {
      return {
        isEdit:false,
        readonly:true,
        index:null,
        editTableItem:'',
        tableItem:{},
        tableData: [{
          date: '2016-5-3',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-5-2',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-5-4',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-5-1',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }]
      }
    }
  }
</script>
<style lang="scss" >
.table{
  position: relative;
}
</style>