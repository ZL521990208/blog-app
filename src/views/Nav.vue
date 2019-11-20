<template>
	<div>
		<el-menu
		  :default-active="activeIndex2"
		  class="el-menu-demo"
		  mode="horizontal"
		  @select="handleSelect"
		  background-color="#CFD8DC"
		  text-color="#795548"
		  active-text-color="#ffd04b">
		  <el-menu-item index="1"><router-link to="/index">主页</router-link></el-menu-item>
		  <el-submenu index="2">
		    <template slot="title">详情</template>			
		    <el-menu-item index="2-1"><router-link to="/article">文章</router-link></el-menu-item>
		    <el-menu-item index="2-2">作者</el-menu-item>
		    <el-menu-item index="2-3">消息</el-menu-item>
		    <el-submenu index="2-4">
		      <template slot="title">个人信息</template>
		      <el-menu-item index="2-4-1">空间</el-menu-item>
		      <el-menu-item index="2-4-2">主页</el-menu-item>
		      <el-menu-item index="2-4-3">修改密码</el-menu-item>
			  
		    </el-submenu>
		  </el-submenu>
		   <el-menu-item index="3"><router-link to="/collection">专题</router-link></a></el-menu-item>
		  <el-menu-item index="4" >联系我们</el-menu-item>
		 
		
		<div class="right">
			<ul v-if="!this.user">
				<li><router-link to="/download">下载APP</router-link></li>
				<li><router-link to="/sign">登录</router-link></li>
			</ul>
			<ul>
				<li v-if="this.user" class="bl-df-right">
					<router-link to="/user"><img :src="user.avatar" class="bl-avatar-normal" /></router-link>
				</li>
			</ul>
		</div>
		</el-menu>
<!-- 
		<header>
			<div class="left">
				<li>
										<router-link to="/index">主页</router-link>
									</li>
									<li>
										<router-link to="/collection">专题</router-link>
									</li>
									<li>
										<router-link to="/article">文章</router-link>
									</li>
									<li>
										<router-link to="/user">作者</router-link>
									</li>
								</div>
								<div class="bl-df-right">
									<ul v-if="!this.user">
										<li><router-link to="/download">下载APP</router-link></li>
										<li><router-link to="/sign">登录</router-link></li>
									</ul>
									<ul>
										<li v-if="this.user" class="bl-df-right">
											<router-link to="/user"><img :src="user.avatar" class="bl-avatar-normal" /></router-link>
										</li>
									</ul>
								</div>
				
		
		</header> -->
		<router-view class="xu-container" />
		
	</div>
		
</template>

<script>
export default {
	data() {
		return {
			user: JSON.parse(localStorage.getItem('user'))
		};
	},
	created() {},
	methods: {}
};
</script>

<style scoped>
	*{
		margin: 0;
		padding: 0;
	}
	#top{
		height: 50px;
		background-color: rgb(131, 53, 109);
		margin-bottom: 10px;
		display: flex;
		justify-content: space-between;
	}
	header{
		position: fixed;
		width: 100%;
		height: 60px;
		background: #008B8B;
		color: #FFF;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.left{
		display: flex;
		flex-direction: row;
		padding-left: 30px;
	}
	li{
		/*去掉圆点*/
		list-style: none;
	}
	.left li{
		margin-right: 10px;
	}
	.right{
		display: flex;
		flex-direction: row-reverse;
		padding-right: 20px;
		text-color:#fff;
		margin-top:10px;
	}
	.right img{
		width: 40px;
		height:40px;
		border-radius: 50%;
	}
	
	.container{
		width: 90%;
		margin: 0 auto;
		background-color: #eee;
		height: 600px;
		padding-top: 15px;
	}
	
</style>