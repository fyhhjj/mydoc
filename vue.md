vue-cli2.+ 搭建脚手架
安装node
npm i webpack -g
npm i vue -g
npm i vue-cli -g
cmd $ vue init webpack demo(项目名称)

$ cd demo 
$ npm install(i)
$ npm i axios
$ npm i 其他配置依赖


vue-cli3.+
npm i @/vue-cli
cmd $ vue create demo
选择需求的配置依赖 上下调整位置，空格选中
cd demo 
npm i axios

# vue 3.0 配置px自动转换rem  postcss-pxtorem
安装依赖
npm i postcss-pxtorem -D

设置规则（更改postcss.config.js）
```
module.exports = {
  plugins: {
    'autoprefixer': {
      browsers: ['Android >= 4.0', 'iOS >= 7']
    },
    'postcss-pxtorem': {
      rootValue: 16,//结果为：设计稿元素尺寸/16，比如元素宽320px,最终页面会换算成 20rem
      propList: ['*']
    }
  }
}
```
src下新建lib/rem.js
```
// 设置 rem 函数
function setRem () {

    // 320 默认大小16px; 320px = 20rem ;每个元素px基础上/16
    let htmlWidth = document.documentElement.clientWidth || document.body.clientWidth;
//得到html的Dom元素
    let htmlDom = document.getElementsByTagName('html')[0];
//设置根元素字体大小
    htmlDom.style.fontSize= htmlWidth/20 + 'px';
}
// 初始化
setRem();
// 改变窗口大小时重新设置 rem
window.onresize = function () {
    setRem()
}
```
main.js中引入rem.js
import './lib/rem.js'

vue 获取元素的方法 ref

router-link 默认to显示，在router.js设置其属性redirect
