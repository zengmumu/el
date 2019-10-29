<template>
    <div>
        <el-dialog title="修改用户" :visible.sync="showEdit.show">
            
            <el-form ref="form" :model="form" label-width="80px">
                <el-form-item label="日期">
                    <el-date-picker type="date" placeholder="选择日期" 
                    v-model="form.date" style="width: 100%;" 
                    format="yyyy 年 MM 月 dd 日"
                    value-format="yyyy-MM-dd">
                    </el-date-picker>
                </el-form-item>
                <el-form-item label="姓名">
                   <el-input v-model="form.name"></el-input>
                </el-form-item>
                 <el-form-item label="地址">
                   <el-input v-model="form.address"></el-input>
                </el-form-item>
            </el-form>

            <div slot="footer" class="dialog-footer">
                <el-button @click="showEdit.show=false">取 消</el-button>
                <el-button type="primary" @click="sureEdit">修改</el-button>
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
    methods:{
        sureEdit(){
            this.showEdit.show=false
            // 关闭弹出框
            this.pform.name = this.form.name;
            this.pform.date = this.form.date;
            this.pform.address = this.form.address;
            // this.pform = this.form;
        }
    },
    // 监听 showEdit 是否发生变化 如果show为zhen 则负责给form
    watch:{
        "showEdit":{
            handler:function(nval,oval){
                if(nval.show){
                    this.form.name = this.pform.name;
                    this.form.date = this.pform.date;
                    this.form.address = this.pform.address;
                }
            },
            deep:true,
        }
    },
    props:['showEdit',"pform"]
}
</script>