<template>
  <div class="tmpl">
      <el-row>
            <div class="btn-border">  
               <el-col :span="5">
                  <div class="btn">
                       <el-button class="btn-size"><i class="el-icon-plus icon-img"></i>新增</el-button>
                       <el-button class="btn-size"><i class="el-icon-check icon-img"></i>全选</el-button>
                       <el-button class="btn-size"><i class="el-icon-delete icon-img"></i>删除</el-button>
                  </div>
               </el-col>
               <el-col :span="3" :offset="16">
                 <div class="btn"><el-input placeholder="请输入搜索内容"  v-model="searchValue" icon="search" :on-icon-click="getlist"></el-input>
                 </div>
               </el-col>
            </div>
      </el-row>
      
     <el-row>
        <el-col :span="24">
           <el-table :data="list" height="400" border style="width: 100%">
                 <el-table-column type="selection" width="55">
                 </el-table-column>
                 <el-table-column prop="title" label="标题" @mouseover="showimg">
                     <el-tooltip class="item" effect="dark" content="Right Center 提示文字" placement="right" :show='isshow'>
                        
                     </el-tooltip>
                 </el-table-column>
                 <el-table-column prop="categoryname" label="所属类别" width="100">
                 </el-table-column>
                 <el-table-column prop="stock_quantity" label="库存" width="80">
                 </el-table-column>
                 <el-table-column prop="market_price" label="市场价" width="80">
                 </el-table-column>
                 <el-table-column prop="sell_price" label="销售价" width="80">
                 </el-table-column>
                 <el-table-column prop="sub_title" label="属性" width="400">
                 </el-table-column>
                 <el-table-column label="操作" width="100">
                     <template scope="scope">
                        <a href="#">修改</a>
                     </template>
                   </el-table-column>
             </el-table>
        </el-col>
     </el-row>
      
      <el-row>
         <div class="btn-border page">
            <el-pagination @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="currentPage4" :page-sizes="[10, 20, 50, 100,200]" :page-size="10" layout="total, sizes, prev, pager, next, jumper" :total="50">
            </el-pagination>
          </div> 
      </el-row>
  </div>
</template>

<script>
  export default{
    data(){
      return{
        searchValue:"",
        isshow:false,
         list:[]
      }
    },
    //获取数据列表
    created(){
      this.getlist();
    },
    methods:{
       getlist(){
         var url='/admin/goods/getlist?pageIndex=1&pageSize=10&searchvalue=';
         this.$http.get(url).then(res=>{
           if(res.data.status==1){
             this.$message.error(res.data.message);
             return;
           }
           this.list=res.data.message;
         });
       },
       showimg(){
         this.isshow=!this.isshow;
       }
    }
  }
</script>
<style scoped>
  
</style>