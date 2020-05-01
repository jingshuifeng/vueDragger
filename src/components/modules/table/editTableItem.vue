<!--
 * @Author: your name
 * @Date: 2020-03-29 13:37:23
 * @LastEditTime: 2020-03-29 21:55:39
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \xuwentest\src\components\modules\editTableItem.vue
 -->
<template>
  <div>
    <el-form class="from" ref="form" :model="sizeForm" label-width="60px">
      <el-form-item label="日期">
        <el-col :span="20">
          <el-date-picker
            :readonly="readonly"
            required
            type="date"
            placeholder="选择日期"
            v-model="sizeForm.date"
            style="width: 100%;"
          ></el-date-picker>
        </el-col>
      </el-form-item>

      <el-form-item label="姓名">
        <el-col :span="20">
          <el-input :readonly="readonly" required :span="10" v-model="sizeForm.name"></el-input>
        </el-col>
      </el-form-item>

      <el-form-item label="省份">
        <el-col :span="20">
          <el-input :readonly="readonly" required v-model="sizeForm.province"></el-input>
        </el-col>
      </el-form-item>
      <el-form-item label="市区">
        <el-col :span="20">
          <el-input :readonly="readonly" required v-model="sizeForm.city"></el-input>
        </el-col>
      </el-form-item>
      <el-form-item label="地址">
        <el-col :span="20">
          <el-input :readonly="readonly" required v-model="sizeForm.address"></el-input>
        </el-col>
      </el-form-item>

      <el-form-item label="邮编">
        <el-col :span="20">
          <el-input :readonly="readonly" required v-model="sizeForm.zip"></el-input>
        </el-col>
      </el-form-item>
      <el-form-item size="large">
        <el-row>
          <el-col :span="1">
            <el-button type="primary" @click="onSubmit">添加/修改</el-button>
          </el-col>
          <el-col :span="1" style="marginLeft:130px;">
            <el-button @click="onSubmitEsc">取消</el-button>
          </el-col>
        </el-row>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  props: {
    tableItem: {
      type: Object
    },
    index: {
      type: Number
    },
    readonly: {
      type: Boolean
    },
    isEdit: {
      type: Boolean
    }
  },
  data() {
    return {
      sizeForm: {
        address: "",
        city: "",
        date: "",
        name: "",
        province: "",
        zip: 200333
      }
    };
  },
  created() {
    if (this.tableItem) {
      this.sizeForm = this.tableItem;
    }
  },
  methods: {
    onSubmit() {
      if (this.isEdit) {
        let date = this.sizeForm.date;
        this.sizeForm.date =
          date.getFullYear() +
          "-" +
          (date.getMonth() + 1) +
          "-" +
          date.getDate();
        this.$emit("submitss", {
          editTableItem: "",
          sizeForm: this.sizeForm,
          index: this.index
        });
      } else {
        if (this.sizeForm.name) {
          let date = this.sizeForm.date;
          this.sizeForm.date =
            date.getFullYear() +
            "-" +
            (date.getMonth() + 1) +
            "-" +
            date.getDate();
          this.$emit("submitss", {
            editTableItem: "",
            sizeForm: this.sizeForm
          });
        } else {
          this.$emit("submitss", {
            editTableItem: ""
          });
        }
      }
    },
    onSubmitEsc() {
      if (!this.sizeForm.date) {
        this.$emit("submitEsc", {
          editTableItem: ""
        });
      } else {
        let date = this.sizeForm.date;
        console.log(date);
        this.sizeForm.date =
          date.getFullYear() +
          "-" +
          (date.getMonth() + 1) +
          "-" +
          date.getDate();
        this.$emit("submitEsc", {
          editTableItem: ""
        });
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.from {
  position: absolute;
  top: 150px;
  left: 0;
  z-index: 100;
  background-color: skyblue;
}
</style>