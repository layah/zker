<template>
    <div class="zk_homebg">
        <div class="bgc"></div>
       <Headers :add="add" :headslogo="headslogo" :name="name" :title="title"></Headers>
        <div class="zk-train-title">
            <h2>{{protject.prolist}}</h2>
            <span>开发工具: {{protject.projsd}}</span>
            <span>项目源代码工程包: {{protject.prsdwe}}</span>
            <span>项目文档清单: {{protject.wordlist}}</span>
            <span>项目安装包: {{protject.extbog}}</span>
        </div>
        <div class="train-head">
            <ul>
                <li class="trabtn" v-for="trab in titlelist" :id="'course'+trab.titlenb">
                    <div class="trabtn-icon"  @click="getcourselist($event)"></div>
                    <p>{{trab.titlename}}</p>
                </li>
            </ul>
            <div class="train-line"></div>
        </div>
        <div class="auto_box">
      <div class="couse_list_box Mtp20" v-for="(couseList,index) in couseList">
        <div class="p_ibt wido25 Mtp20 Mlf15 Mrt25 fl">
          <div class="p_ibt posr" >
            <img :src="couseList.couseImg" alt="" width='300' />
            <span class="couse_name">{{couseList.couseName}}</span>
          </div>
        </div>
        <div class="p_ibt Mtp20 wido70">
          <div class="F18 courseName" :data-index="couseList.id">{{couseList.couseName}}</div>
          <div class="F14 Mtp20 Line18 het60">{{couseList.couseIntr}}</div>
        </div>
        <ul class="F0 couses_icon_box ">
          <li class="p_ibt Mrt60" v-for="(couseICon,index) in couseList.couseICon">
            <div class="couses_icon " :class="'couses_icon_'+(index+1)">
              <a href="javascript:;" class="scale_icon" :data-index="(index+1)" @click="showchapter($event)"></a>
            </div>
            <div class="F12 wid50 Mtp10 Center">{{couseICon}}</div>
          </li>
        </ul>
      </div>
    </div>
    <Footers :cursor="cursor"></Footers>
    <div class="scaleBox" id="couseList">
      <div class="table">
        <div class="table_cell">
          <div class="scaleBox_cont p_ibt Tleft posr">
            <div class="Mtp30 Mlf30 Mrt30 Mbm30">
              <div class="F24 alert_title Pbm30"></div>
              <div class=" targetList Pbm15">
                <div class="F16 targeIcon Mlf20">教学目标</div>
                <ul class="Mlf30 F0">
                  <li class="F14 list_disc Plf20 Prt20 p_ibt WTO" v-for="name in chapter.targetNm">{{name}}</li>
                </ul>
              </div>
              <div style="height:256px;overflow-y:auto;" class=" Mtp30 border1 scrollBox">
                <div class="tabel Center ">
                  <div class="thead ">
                    <div class="color_f F0">
                      <div class="p_ibm widoo30 Tleft F14 bor_right Plf15">章节名称</div>
                      <div class="p_ibm wido10 F14 bor_right">学时</div>
                      <div class="p_ibm wido20 F14 bor_right">配置的案例套件</div>
                      <div class="p_ibm wido10 F14 bor_right">说明案例</div>
                      <div class="p_ibm wido10 F14 bor_right">应用案例</div>
                      <div class="p_ibm wido10 F14 bor_right">综合案例</div>
                      <div class="p_ibm wido10 F14 bor_right">企业案例</div>
                    </div>
                  </div>
                  <div class="t_body">
                    <div class="t_row F0" v-for="(chapterNm,index) in  chapter.chapterNm">
                      <div class="p_ibm widoo30 Tleft F14 bor_right WTO">
                        <span class="Plf15" v-text="index>=9?index+1:('0'+(index+1))"></span>
                        <span class="Mlf5">{{chapterNm.chapName}}</span>
                      </div>
                      <div class="p_ibm wido10 F14 bor_right">{{chapterNm.times}}</div>
                      <div class="p_ibm wido20 F14 bor_right">{{chapterNm.case}}</div>
                      <div class="p_ibm wido10 F14 bor_right">{{chapterNm.stateCase}}</div>
                      <div class="p_ibm wido10 F14 bor_right">{{chapterNm.apply}}</div>
                      <div class="p_ibm wido10 F14 bor_right">{{chapterNm.zh}}</div>
                      <div class="p_ibm wido10 F14 ">{{chapterNm.firm}}</div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="close_btn_box posa">
              <a href="javascript:;" class="p_ibt alert_close_btn" v-on:click="alertClose()"></a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="scaleBox posr" id="pdfBox">
      <div id="scaleBox"></div>
      <div class="close_btn_box" style="right: 2%;top:4%">
        <a href="javascript:;" class="p_ibt alert_close_btn" v-on:click="alertClose()"></a>
      </div>
    </div>
    <div class="scaleBox" id="videoBox">
      <div class="table">
        <div class="table_cell">
          <div class="scaleBox_cont p_ibt Tleft F0 posr" style="min-height:600px;">
            <div class="Mtp30 Mlf25 Mbm30 p_ibt wido65" style="background:#000;height:570px;">
              <video id="example_video_1" class="videoBox" controls preload="none" width="100%" height="100%">
            </div>
            <div class="p_ibt wido30 color_f  Mtp30 F14 video_list">
              <div class="Mlf15 Mrt15 Mtp20 F14 color_9  border_bm1">
                <div class="p_ibm border_bm2 Pbm15">
                  视频列表
                </div>
              </div>
              <div class="Mtp25 color_92 F14 Mlf15 Mrt15">
                第一章 Java基本语法
              </div>
              <ul class="v_list">
                <li class="color_d" v-for="video in video" :data-src=(video.srcV)>
                  <span class="p_ibm play_icon Mlf15"></span>
                  <span class="Mlf10 wid188 WTO p_ibm">{{video.name}}</span>
                  <span class="Mlf10">{{video.times}}</span>
                </li>
              </ul>
            </div>
            <div class="close_btn_box posa">
              <a href="javascript:;" class="p_ibt alert_close_btn" v-on:click="alertClose()"></a>
            </div>
          </div>

        </div>
      </div>
    </div>

    </div>
</template>

<script>
import Headers from '../../components/Header-con.vue';
import Footers from '../../components/Footer-two.vue';
import PDFObject from'../../assets/js/pdfobject.min.js';
export default{
    components:{
        Headers,
        Footers
    },
     data() {
        return {
            add:"/#",
            headslogo:"/src/assets/images/logo-java.png",
            name:"Java程序设计基础",
            title:'企业综合案例',
            cursor:7,
            protject:{},
            titlelist:[],
            couseList: [],
            couseTitle: "",
            CorseName:"",
            chapter:{},
            video:[]
        }
    },
    watch: {
        CorseName: function() {
            return this.CorseName;
        }
    },
     methods: {
                getcourselist: function(event) {
                    var coursestr = $(event.target).parents()[0].id;
                    var coursenm = coursestr.substr(coursestr.length-1);
                    this.$http.get('src/assets/json/classicProject'+coursenm+'.json').then(function(data) {
                        this.couseTitle = data.data.data.couseTitle;
                        this.couseList = data.data.data.couserList;
                    })
                },
                getTitlelist: function() {
                    this.$http.get('src/assets/json/titlist.json').then(function(res) {
                        this.titlelist = res.data.titlist;
                        this.protject = res.data.project
                    })
                },
                // ----------------------------------------------------------------------
                getList: function() {
                this.$http.get('src/assets/json/classicProject1.json').then(function(data) {
                    this.couseTitle = data.data.data.couseTitle;
                    this.couseList = data.data.data.couserList;
                })
                },
                alertClose: function(event) {
                $(".scrollBox").scrollTop(0);
                $('.scaleBox').hide();
                document.getElementById("example_video_1").pause();
                },
                showppd: function() {
                PDFObject.embed("src/assets/ppdf.pdf", "#scaleBox", {
                    height: "100%"
                })
                },
                showchapter: function(event) {
                var _this = this;
                var courseName = $(event.target).parents(".couses_icon_box").siblings()
                    .find(".courseName")
                var val = courseName.text();
                var indexNm = courseName.data("index");
                if ($(event.target).data("index") === 1) {
                    $.get('src/assets/json/chapter' + indexNm + '.json').then(function(
                    data) {
                    _this.chapter = data;
                    })
                    $("#couseList").show();
                    $(".alert_title").text(val)
                } else if ($(event.target).data("index") === 5) {
                    $.get('src/assets/json/video.json').then(function(data) {
                    _this.video = data.videoList;
                    });
                    $("#videoBox").show();
                    $(".color_d").removeClass("active1");
                    document.getElementById("example_video_1").src="";
                    document.getElementById("example_video_1").autoplay = true;
                    document.getElementById("example_video_1").load()
                } else {
                    $("#pdfBox").show();
                }
                }
            },
            mounted: function() {
                this.getList();
                this.showppd();
                this.getTitlelist();
            },
            updated:function(){
                $('.v_list').on("click", "li", function() {
                var SrcV = $(this).data("src");
                $(this).addClass("active1").siblings().removeClass("active1");
                document.getElementById("example_video_1").src = SrcV;
                })
            // ------------------------------
                var trwidth = $(".train-head").width();
                var trnum = $('.trabtn').length;
                var trwid;
                if($(window).width() > 1024) {
                    trwid = trwidth/trnum/40;
                }else if ($(window).width() <= 1024 && $(window).width() > 768) {
                    trwid = trwidth/trnum/30;
                }else {
                    trwid = trwidth/trnum/22;
                }
                $('.trabtn').css('width',trwid+"em");
                $(".trabtn-icon").on("click",function() {
                      $(this).css({"background":"#1a9bfc"}).parents().siblings().find(".trabtn-icon").css({"background":"#ccc"});
                })
            }
    }
</script>

<style scoped>
    .zk_homebg {
        width: 100%;
        overflow: hidden;
    }
    .bgc {
        background-image: url(../../assets/images/bg2j.jpg);
        background-size: cover;
        width: 100%;
        height: 100%;
        position: fixed;
        z-index: -1;
    }
    .videoBox{
      height:570px;
      background:#000 url(../../assets/images/timg.gif) no-repeat center;
    }
    .zk-train-title {
        width: 1200px;
        height: 110px;
        margin: 20px auto 0;
        text-align: center;
        border: 1px solid #eee;
        border-radius: 10px;
        background-color: #f6f6f6;
    }
    .zk-train-title h2 {
        font: 18px/66px microsoft yahei;
    }
    .zk-train-title span {
        padding: 0 55px;
    }

.train-head {
    width: 1200px;
    height: 110px;
    margin: 0 auto;
    overflow: hidden;
    position: relative;
}

.zk_homebg .train-head ul {
    font-size: 40px;
}

.train-head .trabtn {
    float: left;
    height: 110px;
    position: relative;
    text-align: center;
}
.train-head .trabtn p {
    padding-top: 89px;
    font-size: 16px;
}
.train-head .trabtn .trabtn-icon {
    width: 42px;
    height: 42px;
    background-color: #ccc;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 5;
    border-radius: 50%;
    box-sizing: content-box;
    border: 4px solid #f1f1f1;
    cursor:pointer;
}
#course1 .trabtn-icon  {
    background-color: #1a9bfc;
}
.train-head .trabtn .trabtn-icon::before {
    content: '';
    width: 18px;
    height: 28px;
    position: absolute;
    top: 7px;
    left: 13px;
    background: url(../../assets/images/Sprite.png) no-repeat -217px -6px;
}
.train-line {
  width: 1200px;
  border-top: 5px solid #e7eaec;
  position: absolute;
  top: 50px;
  z-index: 2;
}

.tabel {
  display: table;
  width: 100%;
}
.widoo30{
  width:30%;
}
.thead {
  width: 100%;
  height: 50px;
  line-height: 50px;
  background: #1a9bfc;
}

.t_row {
  /*display: table-row;*/
  width: 100%;
  min-height: 40px;
  line-height: 40px;
  border-bottom: 1px solid #ddd
}

.t_row:nth-child(even) {
  background: #f6f6f6;
}

.color_f {
  color: #fff
}

.bor_right {
  border-right: 1px solid #e5e5e5
}

.border1 {
  border: 1px solid #ddd
}

.pdfobject-container {
  height: 500px;
}

.pdfobject {
  border: 1px solid #666;
}

.pdfobject-container {
  height: 100%;
}

.table {
  display: table;
  height: 100%;
}

.wid188 {
  width: 188px;
}

.video_list {
  height: 570px;
  background: #333;
}

.v_list {
  height: 468px;
  overflow-y: auto;
}

.v_list>li {
  height: 50px;
  line-height: 50px;
  cursor: pointer;
}

.v_list>li:hover {
  background: #404040;
}

.active1 {
  background: #404040;
}

.play_icon {
  border-width: 8px 0px 8px 13px;
  border-color: transparent transparent transparent #929292;
  border-style: solid;
  height: 0px;
}

.color_92 {
  color: #929292
}

.color_d {
  color: #ddd;
}

.border_bm1 {
  border-bottom: 1px solid #404040;
}

.border_bm2 {
  border-bottom: 2px solid #2fb3ff
}

.wido65 {
  width: 65%;
}

.wido35 {
  width: 35%
}

.F24 {
  font-size: 24px;
}

.targetList {
  min-height: 140px;
  background: #f6f6f6;
}

.targeIcon {
  height: 40px;
  line-height: 40px;
  padding-left: 30px;
  background: url(../../assets/images/couse_icon.png)no-repeat 3px -382px;
}

.list_disc {
  width: 180px;
  background: url(../../assets/images/disc.png) no-repeat left center;
}

.table_cell {
  display: table-cell;
  vertical-align: middle;
  text-align: center;
}

.scaleBox {
  position: fixed;
  display: none;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  z-index: 100;
}

.alert_close_btn {
  width: 40px;
  height: 40px;
  background: url(../../assets/images/Sprite.png)no-repeat 0 -250px;
}

.scaleBox_cont {
  width: 1000px;
  margin: 0 auto;
  border-radius: 8px;
  background: #fff;
}

.auto_box {
  width: 1200px;
  margin-left: auto;
  margin-right: auto;
  min-height: 60px;
}

.couse_list_box {
  width: 100%;
  height: 250px;
  border-radius: 8px;
  background: #fff;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1)
}

.couse_name {
  position: absolute;
  top: 40%;
  left: 0;
  display: block;
  width: 100%;
  height: 48px;
  line-height: 48px;
  color: #fff;
  font-size: 20px;
  text-align: center;
  background: rgba(0, 0, 0, .6);
}

.het60 {
  height: 60px;
}

.wido70 {
  width: 70%;
}

.wid50 {
  width: 50px;
}

.couses_icon {
  position: relative;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: url(../../assets/images/couse_icon.png)no-repeat;
  cursor: pointer;
}

.couses_icon:hover .scale_icon {
  display: block;
}


.couses_icon_1{
  background-position: 0 -59px;
}
.couses_icon_2 {
  background-position: 0 -272px;
}
.couses_icon_3 {
  background-position: 0 -328px;
}

.couses_icon_4 {
  background-position: -56px -328px;
}
.couses_icon_5 {
  background-position: 0 -113px;
}
.close_btn_box {
  position: absolute;
  right: -15%;
  z-index: 100;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 50%;
  top: 0%;
}

.scale_icon {
  position: absolute;
  display: none;
  width: 50px;
  height: 50px;
  border-radius: 50px;
  background: url(../../assets/images/couse_icon.png)no-repeat -79px 15px;
  background-color: rgba(0, 0, 0, 0.6)
}

.couses_icon_box>li:last-child {
  margin-right: 0
}

@media only screen and (min-width: 1024px) {
    .auto_box {
        width: 1200px;
    }
    .actual_list:nth-child(4n) {
        margin-right: 0
    }
    .actual_list {
        margin-right: 26px;
    }
}

;
@media only screen and (min-width: 768px) and (max-width: 1024px) {
  .auto_box {
    width: 960px;
  }
  .close_btn_box {
    right: -2%;
    top: -3%;
  }
  .wido25 {
    width: 30%
  }

  .wido70 {
    width: 65%
  }

  .scaleBox_cont {
    width: 95%
  }
    .zk-train-title {
        width: 900px;
    }
    .zk-train-title span {
        padding: 0 20px;
    }
    .zk_homebg .train-head {
        position: relative;
        margin: 0 auto;
        width: 900px;
    }
    .zk_homebg .train-head ul {
        font-size:  30px;
    }
    .zk_homebg .train-head .train-line {
        width: 900px;
    }
}

;
@media only screen and (max-width: 768px) {
  .auto_box {
    width: 700px;
  }
  .wido65 {
    width: 53%;
  }

  .scaleBox_cont >.wido30{
    width:40%;
  }
  .wido25 {
    width: 43%
  }

  .wido70 {
    width: 48%
  }

  .couse_list_box {
    height: 100%;
    padding-bottom: 20px;
  }

  .couses_icon_box {
    text-align: center;
    margin-top: 20px;
  }

  .couses_icon_box>li {
    margin-right: 100px;
  }

  .het60 {
    height: 210px;
  }
  /*.table_cell .Mlf15{margin-left: 0}*/
  .close_btn_box {
    right: -14px;
    top: -20px;
  }
     .zk-train-title {
        width: 650px;
        height: 150px;
    }
    .zk-train-title span {
        float: left;
        width: 300px;
        text-align: left;
        padding: 5px 40px;
        margin-left: 20px;
    }
    .zk_homebg .train-head {
        width: 660px;
    }
    .zk_homebg .train-head ul {
        font-size: 22px;
    }
    .zk_homebg .train-head .train-line {
        width: 660px;
    }
}

@media screen and (max-height: 768px) {
    .header_top {
        padding-bottom: 0;
    }
    .Mtp35 {
        margin-top: 10px;
    }
    .Ptp40 {
        padding-top: 10px;
    }
    .tip_state {
        height: 75px;
    }

}
</style>
