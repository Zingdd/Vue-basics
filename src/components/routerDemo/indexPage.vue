<template>
  <div>
    <h1>{{ msg }}</h1>
	<h3>生命周期看 HelloWorld 组件控制台</h3>
	<hr>
	<el-container>
		<el-aside>
      <el-menu class="el-menu-vertical-demo">
        <el-submenu index="1" class="left">
          <template slot="title">
            <i class="el-icon-printer"></i>
            <span>vue基础</span>
          </template>
          <el-menu-item index="1-1"><router-link to="/HelloWorld">普通路由</router-link></el-menu-item>
          <el-menu-item index="1-2"><router-link :to="/track/+id">动态路由</router-link></el-menu-item>
          <el-menu-item index="1-3"><router-link :to="{name: 'Child'}">嵌套路由</router-link></el-menu-item>
          <el-menu-item index="1-4"><span class="alter" @click="goValue">路由传参</span></el-menu-item>
          <el-menu-item index="1-5"><router-link to="/vueBasicsPage">组件页面</router-link></el-menu-item>
          <el-menu-item index="1-6"><router-link to="/vuexDemo">状态管理器</router-link></el-menu-item>
          <el-menu-item index="1-7"><router-link to="/video">视频组件</router-link></el-menu-item>
        </el-submenu>
        <el-menu-item index="2" class="left">
          <i class="el-icon-menu"></i>
          <span slot="title"><router-link to="/table">列表</router-link></span>
        </el-menu-item>
      </el-menu>
		</el-aside>
		<el-main>
			<router-view/>
		</el-main>
	</el-container>
  </div>
</template>

<script>


import ElSubmenu from "../../../node_modules/element-ui/packages/menu/src/submenu.vue";

export default {
  components: {ElSubmenu},
  name: 'RouteDemo',
	data () {
		return {
			msg: 'vue Router',
			id:123,        //动态路由，命名路由 传值132，返回个人信息 张三 男，否则 李梅 女
		}
	},
	methods:{
		goValue () {
			// 编程式 路由传参，query 和 params 两种 ； query 在地址栏可以看到，params 地址栏看不到
			// 对应组件取值：$route.params.code 或者  $route.query.code
			this.$router.push({
				name:'HelloWorld',
				params:{
					code:123
				}
			})
		},
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .left a {
    padding-left: 15px;
  }
  .left .alter {
    padding-left: 15px;
  }
  .is-active > a {
    color: #409EFF;
  }
  .el-menu-vertical-demo {
    text-align: left;
  }
</style>
