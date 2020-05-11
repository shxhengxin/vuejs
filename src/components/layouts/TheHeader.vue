<template>
  <div class="navbar navbar-default topnav">
      <div class="container" >
          <div class="navbar-header">
              <button type="button" class="navbar-toggle" @click="toggleNav">
                  <span class="sr-only">Toggle navigation</span>
                  <span class="icon-bar"></span>
                  <span class="icon-bar"></span>
                  <span class="icon-bar"></span>
              </button>

              <router-link to="/" class="navbar-brand">
                  <span class="title">{{ logo.title }}</span>
                  <img :src="logo.src" :alt="logo.title">
              </router-link>


          </div>

          <div id="top-navbar-collapse" :class="['collapse', 'navbar-collapse', { in: showCollapsedNav }]">
              <ul class="nav navbar-nav">
                  <li v-for="(item,index) in navList" :class="{active: index === activeNavIndex}">
                      <a href="#" @click="changeNavIndex(index)">{{ item }}</a>
                  </li>
              </ul>
              <!-- 入口组件 -->
              <div class="navbar-right">
                  <TheEntry></TheEntry>
              </div>
          </div>


      </div>
  </div>
</template>

<script>
    import TheEntry from "./TheEntry";
    export default {
        name: "TheHeader",
        components: {TheEntry},
        data() {
            return {
                logo:{
                    src:`${this.uploadsUrl}sites/ByvFbNlQYVwhvTyBgLdqitchoacDNznN.jpg`,
                    title: 'VuejsCaff'
                },
                navList:['社区','头条','问答','教程'],
                activeNavIndex:0,
                showCollapsedNav:false
            }
        },
        methods:{
            changeNavIndex(index){
                this.activeNavIndex = index
            },
            toggleNav() {
                this.showCollapsedNav = !this.showCollapsedNav
            }
        },
        beforeCreate() {// 生命周期钩子的一部分，在实例初始化之后，数据观测之前被调用
            this.uploadsUrl = 'https://vuejscaff.com/uploads/';
        }
    }
</script>

<style scoped>
.title {display: none}
.navbar-default .navbar-nav > .active > a { background: rgba(0,0,0,.03);}
</style>
