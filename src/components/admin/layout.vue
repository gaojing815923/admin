<template>
  <div class="tmpl">
      <el-row>
         <el-col :span="leftcol">
           <img src="../../../statics/imgs/logo.png" alt="" class="menu-img">
            <div class="layout menu">
                <el-menu default-active="1-2" class="el-menu-vertical-demo" :collapse="iscollapse">
                    <el-submenu index="1">
                       <template slot="title"><i class="el-icon-message"></i>购物商城</template>
                       <el-menu-item-group>
                       
                         <el-menu-item index="1-1"><i class="el-icon-document icon-img"></i>内容管理</el-menu-item>
                         <el-menu-item index="1-2"><i class="el-icon-document icon-img"></i>类别管理</el-menu-item>
                         <el-menu-item index="1-3"><i class="el-icon-document icon-img"></i>评论管理</el-menu-item>
                       </el-menu-item-group>
                      </el-submenu>
                      <el-submenu index="2">
                       <template slot="title"><i class="el-icon-message"></i>订单管理</template>
                       <el-menu-item-group>
                         <el-menu-item index="2-1"><i class="el-icon-document icon-img"></i>订单列表</el-menu-item>
                       </el-menu-item-group>
                      </el-submenu>
                   </el-menu>
            </div> 
         </el-col>
         <el-col :span="rightcol">
            <div class="top-right topbg">
               <el-row>
               <el-col :span="1">
                 <div class="topbg">
                   <i class="el-icon-menu area" @click="dropmenu"></i>
                 </div>
               </el-col>
               <el-col :span="23" >
                 <div class="top-right">
                    <span class="hello">你好,admin</span>
                   <el-dropdown>
                     <span class="el-dropdown-link">功能<i class="el-icon-caret-bottom el-icon--right"></i></span>
                      <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item>预览网站</el-dropdown-item>
                        <el-dropdown-item>修改密码</el-dropdown-item>
                        <el-dropdown-item>注销登录</el-dropdown-item>
                       </el-dropdown-menu>
                     </el-dropdown>
                 </div>
               </el-col>
              </el-row> 
            </div>
            <el-row>
              <el-col>
                 <div class="topbg top-right top-nav">
                 <el-breadcrumb separator="/">
                   <el-breadcrumb-item :to="{ path: '/' }"><a href="javascript:void(0)">知识内容</a></el-breadcrumb-item>
                   <el-breadcrumb-item><a href="javascript:void(0)">首页</a></el-breadcrumb-item>
                   <el-breadcrumb-item><a href="javascript:void(0)">内容管理</a></el-breadcrumb-item>
                 </el-breadcrumb>
              </div>
              </el-col>
            
            </el-row>
            
            <el-row>
                <el-col :span="24">
                        <!-- 利用vue-router进行填充 -->
                        <router-view></router-view>
                    </el-col>
            </el-row>
         </el-col>
      </el-row>
      
  </div>
</template>

<script>
  export default{
    data(){
      return{
        
        iscollapse:false,
        //设置左边菜单栏的宽度
        leftcol:4,
        //设置右边内容的宽度
        rightcol:20
      }
    },
    methods:{
      dropmenu(){
       this.iscollapse=!this.iscollapse;
       if(this.iscollapse){
           this.leftcol=1,
           this.rightcol = 23;
       }else{
         this.leftcol=4,
         this.rightcol = 20;
       }
      }
    }
  }
</script>
<style scoped>
  
</style>
