<template>
  <div class="container" id="container">
        <aside class="left-bar" id="leftBar">
            <div class="title">
                <p>IDMISS导航</p>
            </div>
            <nav class="nav">
                <div class="item active"><a href=""><i class="iconfont icon-daohang2"></i>导航列表</a><i class="line"></i></div>
                <ul class="nav-item" id="navItem">
                    <li v-for="(data, index) in dataList" v-show="searchFilter1(data)"><a :href="'#'+data.puri" :class="('#'+data.puri)==phash?'active':''">
                        <i class="iconfont" :class="'icon-'+data.puri"></i>{{data.pname}}</a></li>
                </ul>
                <div class="item comment"><a target="_blank" href="http://www.idmiss.com/message"><i class="iconfont icon-liuyan"></i>留言</a></div>
            </nav>
        </aside>
        <section class="main">
            <div id="mainContent">
                
                <!-- 手机端菜单 -->
                <div id="menu-box">
                   <div id="menu" @click="oMenu">
                       <input type="checkbox" id="menu-form">
                       <label for="menu-form" class="menu-spin">
                        <div class="line diagonal line-1"></div>
                        <div class="line horizontal"></div>
                        <div class="line diagonal line-2"></div>
                      </label>
                    </div>
                </div>
                <div class="search-box">
                    <input placeholder="Search" type="search" v-model="searchData">
                </div>

                
                <!-- 开发社区 -->
                <div class="box" v-for="(data, pindex) in dataList" v-if="searchFilter1(data)">
                    <a href="#" :name="data.puri"></a>
                    <div class="sub-category">
                        <div><i class="iconfont " :class="'icon-'+data.puri"></i>{{data.pname}}</div>
                    </div>
                    <div>
                        <a v-for="cdata in data.data" target="_blank" :href="cdata.uri" v-if="searchFilter(cdata,pindex)">
                            <div class="item">
                                <div class="logo" v-if="cdata.icon&&cdata.icon!=''"><img :src="cdata.icon" alt="cdata.name"> {{cdata.name}}</div>
                                <div class="no-logo" v-if="!cdata.icon||cdata.icon==''">{{cdata.name}}</div>
                                <div class="desc" v-if="cdata.desc&&cdata.desc!=''">{{cdata.desc}}</div>
                            </div>
                        </a>
                    </div>
                </div>
                <footer class="footer">
                    <div class="copyright">
                        <div>
                            Copyright © 2018- 2050 京ICP备18015788号-3
                            <a href="http://www.idmiss.com">IDMISS导航</a>
                        </div>
                    </div>
                </footer>
                <div @click="toTop" ><svg class="Zi Zi--BackToTop" title="回到顶部" fill="currentColor" viewBox="0 0 24 24" width="24" height="24"><path d="M16.036 19.59a1 1 0 0 1-.997.995H9.032a.996.996 0 0 1-.997-.996v-7.005H5.03c-1.1 0-1.36-.633-.578-1.416L11.33 4.29a1.003 1.003 0 0 1 1.412 0l6.878 6.88c.782.78.523 1.415-.58 1.415h-3.004v7.005z"></path></svg></div>
              </div>
        </section>
      </div>

</template>

<script>
  import "../assets/css/style.css"
  import "../assets/css/iconfont.css"
export default {
  name: 'Daohang',
  data () {
    return {
        searchData:null,
    phash:this.$route.hash,        // 开发社区  链接 uri，名称name，图标icon，描述desc
      dataList: [{
    pname: '破解软件',
    puri: 'bbs',
    data: [{
        name: 'TeamViewer',
        uri: ' https://pan.baidu.com/s/16qAjbXoZmyUnsOknGhPDQw',
        icon: 'http://images.idmiss.com/image/logo/1.png',
        desc: 'TeamViewer 大神破解的企业版TeamViewer，可随时换ID，提取码: mgeb'
    },
    {
        name: 'Xshell',
        uri: 'https://pan.baidu.com/s/1E-MoaFOJx41hKYZ9sH1dFg',
        icon: 'http://images.idmiss.com/image/logo/2.png',
        desc: 'Xshell 破解版 ，提取码: i63f'
    },{
        name: 'ShadowsocksR',
        uri: 'https://pan.baidu.com/s/1q99qGOyRN4EKi6sk4QftZw',
        icon: 'http://images.idmiss.com/image/logo/3.png',
        desc: 'ShadowsocksR 包含win/mac/android版本，iOS下载Potatso Lite，提取码: 6aah'
    }, {
        name: 'Navicat Premium',
        uri: 'https://pan.baidu.com/s/1SXrTc-LgMMHZTF8QH9oCRA',
        icon: 'http://images.idmiss.com/image/logo/4.jpg',
        desc: 'Navicat Premium 破解含注册机，数据可视化管理工具，提取码: ansj'
    }, {
        name: 'PS CC 2019',
        uri: 'https://github.com/',
        icon: 'http://images.idmiss.com/image/logo/5.png',
        desc: 'Photoshop CC 2019破解版'
    }]
}
, {
    pname: '实用工具',
    puri: 'tools',
    data: [{
        name: '百度云下载工具',
        uri: 'https://www.speedpan.com/'
    }, {
        name: 'Google Chrome 国内镜像下载地址',
        uri: 'https://api.shuax.com/tools/getchrome'
    }, {
        name: '图片无损压缩',
        uri: 'https://tinypng.com/'
    }, {
        name: 'Firefox 接口测试插件RESTED',
        uri: 'https://addons.mozilla.org/zh-CN/firefox/addon/rested/'
    }, {
        name: '超轻量屏幕录制 ScreenToGif',
        uri: 'https://www.screentogif.com'
    }, {
        name: 'bootstrap可视化布局',
        uri: 'http://www.ibootstrap.cn/'
    }, {
        name: '网页配色工具',
        uri: 'http://www.peise.net/tools/web/'
    }, {
        name: '在线PS',
        uri: 'http://www.uupoop.com/'
    }, {
        name: '动态图像生成器',
        uri: 'https://dummyimage.com/'
    }, {
        name: '美图秀秀在线图片处理',
        uri: 'http://xiuxiu.web.meitu.com/main.html'
    }, {
        name: '二维码在线生成',
        uri: 'https://cli.im/deqr'
    }, {
        name: 'Markdown在线编辑器',
        uri: 'https://www.zybuluo.com/mdeditor'
    }, {
        name: '短网址生成',
        uri: 'http://dwz.wailian.work/'
    }]
}, {
    pname: '学习下载',
    puri: 'download',
    data: [{
                name: 'AUXPI',
                uri: 'https://github.com/aimerforreimu/AUXPI',
                desc: '基于 API 的简单图床应用,集合多家 API 的新一代图床'
            },{
                name: 'CSS Inspiration',
                uri: 'https://github.com/chokcoco/CSS-Inspiration',
                desc: 'CSS 的使用和学习的示例代码'
            },{
                name: 'WEB 入门学习',
                uri: 'https://github.com/qianguyihao/Web',
                desc: 'Web前端入门和进阶学习笔记，超详细的前端学习图文教程。从零开始学前端，做一个Web全栈工程师。'
            },{
                name: 'Python爬虫框架',
                uri: 'https://github.com/xianhu/PSpider',
                desc: '简单易用的Python爬虫框架'
            },{
                name: 'webmagic',
                uri: 'https://github.com/code4craft/webmagic/blob/master/README-zh.md',
                desc: 'webmagic是一个开源的Java垂直爬虫框架'
            },{
                name: '弹出层-对话框',
                uri: 'https://github.com/aui/artDialog',
                desc: 'artDialog——经典、优雅的网页对话框控件。'
            },{
                name: '响应式用户交互组件库UI',
                uri: 'https://github.com/bh-lay/UI',
                desc: '前端公用的视觉交互类公用组件。'
            },{
                name: 'sweetalert-对话框',
                uri: 'https://github.com/t4t5/sweetalert',
                desc: '漂亮的弹框组件。'
            }]
}, {
    pname: '开发文档',
    puri: 'docs',
    data: [{
        name: '微信小程序',
        uri: 'https://developers.weixin.qq.com/miniprogram/dev/api/',
        icon: 'http://images.idmiss.com/image/daohang/weixin-api.png',
        desc: '微信小程序开发文档'
    },{
        name: 'jQuery',
        uri: 'http://jquery.cuishifeng.cn/index.html',
        icon: 'http://images.idmiss.com/image/daohang/jquery.png',
        desc: '优秀的JavaScript代码库。'
    }, {
        name: 'Bootstrap',
        uri: 'http://v3.bootcss.com/',
        icon: 'http://images.idmiss.com/image/daohang/bootstrap-favicon.png',
        desc: '基于HTML/CSS/Javscript的前端框架。'
    }, {
        name: 'Vue.js',
        uri: 'https://cn.vuejs.org/v2/guide/',
        icon: 'http://images.idmiss.com/image/daohang/vue-favicon.png',
        desc: '构建数据驱动的web界面的渐进式框架。'
    }]
}
, {
    pname: '技术博客',
    puri: 'blog',
    data: [
    {
        name: '纯洁的微笑',
        uri: 'http://www.ityouknow.com/',
        icon: 'http://images.idmiss.com/image/daohang/ityouknow.jpg',
        desc: 'Spring Boot , Spring Cloud'
    },{
        name: '阿里巴巴国际UED团队',
        uri: 'http://www.aliued.com/',
        icon: 'http://images.idmiss.com/image/daohang/aliued.png',
        desc: '我们，一群UEDers，来自阿里巴巴国际UED团队。'
    },{
        name: '美团技术团队博客',
        uri: 'https://tech.meituan.com/',
        icon: 'http://images.idmiss.com/image/daohang/meituan.png',
        desc: '美团技术团队博客，分享技术文章。'
    },{
        name: '腾讯 AlloyTeam 团队',
        uri: 'http://www.alloyteam.com/',
        icon: 'http://images.idmiss.com/image/daohang/alloyteam-favicon.png',
        desc: '腾讯Web前端团队，代表作品WebQQ，致力于前端技术的研究。'
    }, {
        name: 'i 笔记 - idmiss',
        uri: 'http://www.idmiss.com/',
        icon: 'http://images.idmiss.com/image/logo/fav.png',
        desc: '一个分享技术的小博客。'
    }, {
        name: 'ISUX',
        uri: 'https://isux.tencent.com/',
        icon: 'http://images.idmiss.com/image/daohang/isux-favicon.png',
        desc: '腾讯社交用户体验设计，简称ISUX，腾讯设计团队网站。'
    }, {
        name: 'FEX',
        uri: 'http://fex.baidu.com/',
        icon: 'http://images.idmiss.com/image/daohang/fex-favicon.png',
        desc: '百度Web前端研发部出品。'
    }, {
        name: '淘宝前端团队（FED）',
        uri: 'http://taobaofed.org/',
        icon: 'http://images.idmiss.com/image/daohang/fed-favicon.png',
        desc: '用技术为体验提供无限可能。'
    }, {
        name: '凹凸实验室',
        uri: 'https://75team.com/',
        icon: 'http://images.idmiss.com/image/daohang/aotu-favicon.png',
        desc: '京东用户体验设计部出品。'
    }, {
        name: '奇舞团',
        uri: 'https://aotu.io/',
        icon: 'http://images.idmiss.com/image/daohang/75team-favicon.png',
        desc: '奇虎360旗下前端开发团队出品。'
    }, {
        name: 'EFE',
        uri: 'http://efe.baidu.com/',
        icon: 'http://images.idmiss.com/image/daohang/efe-favicon.png',
        desc: '由百度多个遵循统一技术体系的前端团队所组成。'
    }]
}, {
    pname: '解决问题',
    puri: 'reference',
    data: [{
            name: 'sublime install 错误问题解决',
            uri: 'http://www.idmiss.com/520'
        },{
            name: 'yum 执行报 python 版本错误问题',
            uri: 'https://www.cnblogs.com/fzw-/p/8179824.html'
        },{
            name: 'Linux yum安装svn',
            uri: 'https://www.linuxidc.com/Linux/2017-10/147871.htm'
        }]
}],
    }
  },
  filters:{
    

  },
  methods: {
    searchFilter1:function(data){
        let that=this;
        if(that.searchData!=null&&that.searchData!=''){
                       for(var i=0;i<data.data.length;i++){
                        if(data.data[i].name.toLowerCase().indexOf(that.searchData.toLowerCase())!==-1 || (data.data[i].desc && data.data[i].desc.toLowerCase().indexOf(that.searchData.toLowerCase())!==-1)){
                             return true;
                        }
                       }
                       return false;
        }else{
                    return true;
                }
    },
    searchFilter:function(cdata,pindex){
        if(this.searchData!=null&&this.searchData!=''){
                        if(cdata.name.toLowerCase().indexOf(this.searchData.toLowerCase())!==-1 || (cdata.desc && cdata.desc.toLowerCase().indexOf(this.searchData.toLowerCase())!==-1)){
                             return true;
                        }else{
                            return false;
                        }
        }else{
                    return true;
                }
    },
    toTop:function(){
      $('html,body').animate({scrollTop:'0px'},800);
    },
    oMenu:function(){
        var oLeftBar = document.getElementById('leftBar');
        var menuFrom = document.getElementById('menu-form');
            if (oLeftBar.offsetLeft == 0) {
                oLeftBar.style.left = -249 + 'px';
            }
            else {
                oLeftBar.style.left = 0;
            }
    },
    judgeWidth:function() {
        var oLeftBar = document.getElementById('leftBar');
        var menuFrom = document.getElementById('menu-form');
            if (document.documentElement.clientWidth > 481) {
                oLeftBar.style.left = 0;
            } else {
                oLeftBar.style.left = -249 + 'px';
            }
        }


  },
  mounted(){
    var oLeftBar = document.getElementById('leftBar');
     var menuFrom = document.getElementById('menu-form');
    var oNavItem = document.getElementById('navItem');
        var aA = oNavItem.getElementsByTagName('a');
        for (var i = 0; i < aA.length; i++) {
            aA[i].onclick = function() {
                for (var j = 0; j < aA.length; j++) {
                    aA[j].className = '';
                }
                this.className = 'active';
                if (oLeftBar.offsetLeft == 0) {
                    if (document.documentElement.clientWidth <= 481) {
                        oLeftBar.style.left = -249 + 'px';
                        menuFrom.checked = false;

                    }
                }
            }
        }

    $(window).scroll(function() {
            if($(window).scrollTop() >= 200){
                $('#fixedBar').fadeIn(300);
            }else{
                $('#fixedBar').fadeOut(300);
            }
        });
        $('#fixedBar').click(function() {
            $('html,body').animate({scrollTop:'0px'},800);
        })

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
    outline: none;
}
input[type=search] {
    -webkit-appearance: textfield;
    -webkit-box-sizing: content-box;
    font-family: inherit;
    font-size: 100%;
}
input::-webkit-search-decoration,
input::-webkit-search-cancel-button {
    display: none; 
}


input[type=search] {
    background: #ededed url(http://images.idmiss.com/image/daohang/search-icon.png) no-repeat 9px center;
    border: solid 1px #ccc;
    padding: 9px 10px 9px 32px;
    width: 55px;
    
    -webkit-border-radius: 10em;
    -moz-border-radius: 10em;
    border-radius: 10em;
    
    -webkit-transition: all .5s;
    -moz-transition: all .5s;
    transition: all .5s;
}
input[type=search]:focus {
    width: 230px;
    background-color: #fff;
    border-color: #66CC75;
    
    -webkit-box-shadow: 0 0 5px rgba(109,207,246,.5);
    -moz-box-shadow: 0 0 5px rgba(109,207,246,.5);
    box-shadow: 0 0 5px rgba(109,207,246,.5);
}


input:-moz-placeholder {
    color: #999;
}
input::-webkit-input-placeholder {
    color: #999;
}
.search-box{
    padding-top:15px;
}
</style>
