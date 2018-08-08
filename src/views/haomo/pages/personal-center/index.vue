<template>
  <div class="manage">
    <div class="left l">
		<div class="nav">
			<ul>
				<router-link v-for="(nav,key) in nav_tree" :key="key" active-class="active" tag="li">
					<p><span>{{nav.name}}</span></p>
					<!-- <ol>
						<router-link tag="li" active-class="active" v-for="(sub,key) in nav.sub_nav" :key="key" :to="sub.path">{{sub.title}}</router-link>
					</ol> -->
				</router-link>
			</ul>
		</div>
    </div>
    <div class="right hid">
		<div class="title">oa管理系统<cite>你好，小明</cite></div>
		<div class="container">
			<router-view></router-view>
		</div>
    </div>
  </div>
</template>

<script>
import http from 'axios'
export default {
  name: 'login',
  // 继承其他组件
  extends: {},
  // 使用其它组件
  components: {},
  data() {
    return {
      nav_tree: null
    }
  },
  computed: {},
  filters: {},
  created() {
    http.get('http://api.haomo-studio.com/org/roles').then(res => {
      console.log(this)
      console.log(res.data)
      // console.log(res.data)
      this.nav_tree = res.data
    })
  },
  methods: {}
}
</script>
<style scoped>
.manage {
  width: 80%;
  height: 100%;
  margin: 0 auto;
  /* position: absolute;
	left: 0;
	top: 0; */
  background: #eee;
}
.left {
  width: 260px;
  height: 100px;
  background: #474747;
}
.right {
  height: 100%;
}
.title {
  height: 64px;
  line-height: 64px;
  background: #fff;
  padding: 0 40px;
  font-size: 18px;
  color: #666;
  overflow: hidden;
}
.container {
  height: 100%;
  padding-bottom: 64px;
  box-sizing: border-box;
  overflow-y: scroll;
}
.logo {
  text-align: center;
  padding: 56px 0 52px 0;
}
.nav ul {
  border-top: solid 2px #bbb;
}
.nav ul > li {
  height: auto;
  cursor: pointer;
}
.nav ul > li.active {
  background: #666566;
}
.nav ul > li p * {
  vertical-align: middle;
}
.nav ul > li p {
  height: 40px;
  line-height: 40px;
  color: #fff;
  border-left: solid 8px transparent;
}
.nav ul > li.active p {
  border-color: #ff404b;
}
.nav ul > li p i {
  display: inline-block;
  width: 60px;
  height: 40px;
  font-size: 18px;
  text-align: center;
}
.nav ul > li p span {
  display: inline-block;
  width: 155px;
  height: 40px;
  font-size: 14px;
}
.nav ul > li p b {
  color: #eee;
  font-size: 18px;
}
.nav ul > li > ol > li {
  padding-left: 68px;
  height: 0px;
  line-height: 30px;
  color: #bbb;
  overflow: hidden;
  transition: all 0.3s ease-in-out;
}
.nav ul > li.active > ol > li {
  height: 30px;
}
.nav ul > li > ol > li.active {
  background: #eee;
  color: #f58c8c;
}
</style>
