<template>
    <div>
        <el-dialog title="添加用户" :visible.sync="showAdd.show">
            <el-form ref="form" :model="form" label-width="80px">
                <el-form-item label="日期">
                    <el-date-picker type="date" placeholder="选择日期" v-model="form.date" style="width: 100%;" format="yyyy 年 MM 月 dd 日"
      value-format="yyyy-MM-dd"></el-date-picker>
                </el-form-item>
                <el-form-item label="姓名">
                   <el-input v-model="form.name"></el-input>
                </el-form-item>
                 <el-form-item label="地址">
                   <el-input v-model="form.address"></el-input>
                </el-form-item>
            </el-form>

            <div slot="footer" class="dialog-footer">
                <el-button @click="showAdd.show=false">取 消</el-button>
                <el-button type="primary" @click="showAdd.show=false;$emit('eventadd',form)">添加</el-button>
            </div>
        </el-dialog>
    </div>
</template>
<script>
export default {
    data(){
        return {
            form:{ 
                date: '',
                name: '',
                address: ''
                }
        }
    },
    props:['showAdd']
}
</script>