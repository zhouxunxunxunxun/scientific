<template>
    <el-table
    :data="tableData"
    style="width: 100%">
    <el-table-column type="expand">
      <template slot-scope="props">
        <el-form label-position="left" inline class="demo-table-expand">
          <el-form-item label="主机名">
            <span>{{ props.row.zhuji_name }}</span>
          </el-form-item>
          <el-form-item label="申请时间">
            <span>{{ props.row.apply_time }}</span>
          </el-form-item>
          <el-form-item label="账户名">
            <span>{{ props.row.apply_name }}</span>
          </el-form-item>
          <el-form-item label="通过时间">
            <span>{{ props.row.applypass_time }}</span>
          </el-form-item>
          <el-form-item label="主机的资源类型">
            <span>{{ props.row.apply_style }}</span>
          </el-form-item>
          <el-form-item label="用途">
            <span>{{ props.row.apply_use }}</span>
          </el-form-item>
          <el-form-item label="剩余时长">
            <span>{{ props.row.apply_day }}天</span>
          </el-form-item>
        </el-form>
      </template>
    </el-table-column>
    <el-table-column
      label="账户名"
      prop="apply_name">
    </el-table-column>
    <el-table-column
      label="主机名"
      prop="zhuji_name">
    </el-table-column>
    <el-table-column
      label="剩余时长"
      prop="apply_day">
    </el-table-column>
  </el-table>

</template>

<script>
export default {
     data() {
      return {
        tableData: []
      }
    },
    created() {
        this.$axios.get("http://222.24.63.61:8080/apply/query1").then((res)=>{
            this.tableData = res.data;
        })
    },
}
</script>

<style scoped>
      .demo-table-expand {
    font-size: 0;
  }
  .demo-table-expand label {
    width: 90px;
    color: #99a9bf;
  }
  .demo-table-expand .el-form-item {
    margin-right: 0;
    margin-bottom: 0;
    width: 50%;
  }
</style>