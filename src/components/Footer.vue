<template>
<div class="zkfoot">
	<div class="zk_footer hidden-md hidden-sm hidden-xs">
    	<ul>
          <li :class="{cur: 1 == cursor}"><router-link to="/basis">摘要信息</router-link></li>
          <li :class="{cur: 2 == cursor}"><router-link to="/logic">逻辑结构</router-link></li>
          <li :class="{cur: 3 == cursor}"><router-link to="/phase">课程清单</router-link></li>
          <li :class="{cur: 4 == cursor}"><router-link to="/jobs">岗位与技能</router-link></li>
          <li :class="{cur: 5 == cursor}"><router-link to="/characteristic">优势与特色</router-link></li>
          <li :class="{cur: 6 == cursor}"><router-link to="/lunbo">配套项目</router-link></li>
          <li :class="{cur: 7 == cursor}"><router-link to="/Laboratory">实验环境</router-link></li>
          <li :class="{cur: 8 == cursor}"><router-link to="/teacher">教师团队</router-link></li>
    	</ul>
  </div>
	<div class="zk_footerpad hidden-lg">
		<div class="zk_footerpad_top">
    	<ul>
           <li :class="{cur: 1 == cursor}"><router-link to="/basis">摘要信息</router-link></li>
           <li :class="{cur: 2 == cursor}"><router-link to="/logic">逻辑结构</router-link></li>
           <li :class="{cur: 3 == cursor}"><router-link to="/phase">课程清单</router-link></li>
           <li :class="{cur: 4 == cursor}"><router-link to="/jobs">岗位与技能</router-link></li>
           <li :class="{cur: 5 == cursor}"><router-link to="/characteristic">优势与特色</router-link></li>
           <li :class="{cur: 6 == cursor}"><router-link to="/lunbo">配套项目</router-link></li>
           <li :class="{cur: 7 == cursor}"><router-link to="/Laboratory">实验环境</router-link></li>
           <li :class="{cur: 8 == cursor}"><router-link to="/teacher">教师团队</router-link></li>
    	</ul>
		</div>
		<div class="zk_footerpad_btm">
					<img @click="touchme"  src="../assets/images/button.jpg" alt="" @blur="everyone" tabindex="1">
		</div>
  </div>
</div>
</template>

<script>
export default {
	props:['cursor'],
	data(){
    return {
    body:$("body").height()
    }
  },
	methods: {
			touchme: function() {
				if( $(window).width() >= 1024) {
						$('.zk_footerpad_top').animate({height:"50px"});
				}else {
						$('.zk_footerpad_top').animate({height:"100px"});
				}

				$('.zk_footerpad_btm').animate({height:"0px"});
			},
			everyone: function() {
				$('.zk_footerpad_top').animate({height:"0px"});
				$('.zk_footerpad_btm').animate({height:"40px"});
			}
	}
};
$(function() {
	window.onresize=function(){
       	$('.zk_footerpad_top').animate({height:"0px"});
				$('.zk_footerpad_btm').animate({height:"40px"});
  }
})
</script>

<style scoped>
	.zkfoot {
		margin-top:  60px;
	}
	.zk_footer {
	  position: fixed;
	  z-index: 100;
	  bottom: 0;
	  height: 50px;
	  width: 100%;
	  background-color: #000;
	}
	.zk_footer ul {
	  width: 1200px;
	  margin: 0 auto;
	}
	.zk_footer ul li {
	  float: left;
	  text-align: center;
	}

	.zk_footer ul li a {
	  display: block;
	  width: 150px;
	  height: 50px;
	  font: 14px/50px microsoft yahei;
	  color: #79808e;
	  text-decoration: none;
	}
	.zk_footer ul li a:hover {
	  color: #fff;
	  background-color: #363641;
	}
	.cur a{
		color: #fff !important;
	  background-color: #363641;
	}
	.zk_footerpad {
	  position: fixed;
	  z-index: 100;
	  bottom: 0;
	  width: 100%;
	  background-color: #333;
	}
	.zk_footerpad .zk_footerpad_top {
	  height: 0px;
		overflow: hidden;
	  /*display: none;*/
	}
	.zk_footerpad .zk_footerpad_top ul {
	  width: 600px;
	  margin: 0 auto;
	  text-align: center;
	}
	.zk_footerpad .zk_footerpad_top ul li {
	  float: left;
	}
	.zk_footerpad .zk_footerpad_top ul li a {
	  display: block;
	  width: 150px;
	  height: 50px;
	  color: #999;
	  text-decoration: none;
	  font: 16px/50px microsoft yahei;
	}
	.zk_footerpad .zk_footerpad_top ul li a:hover {
	  color: #fff;
	}
	.zk_footerpad .zk_footerpad_btm {
	  z-index: 10;
	  height: 40px;
	  text-align: center;
	}
	.zk_footerpad .zk_footerpad_btm img {
	  cursor: pointer;
	}
	@media only screen and (min-width: 768px) and (max-width: 1024px) {
		.zk_footerpad .zk_footerpad_top ul {
			width: 600px;
		}
		.zkfoot {
			margin-top:  30px;
		}
		.zk_footerpad .zk_footerpad_top ul li a {
			width: 150px;
		}
	}
		@media only screen and (min-width: 1024px) {
		.zk_footerpad .zk_footerpad_top ul {
			width: 1000px;
		}
		.zk_footerpad .zk_footerpad_top ul li a {
			width: 125px;
		}
	}
</style>
