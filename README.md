# jingo 国际版 前端静态页面 说明

- 加入 `BrowerSync`  进行浏览器同步

在每个html 页面加入了 代码 可进行浏览器同步修改 不用刷新浏览器

```
<!--browserSync 测试 -->
<script id="__bs_script__">//<![CDATA[
document.write("<script async src='http://HOST:3000/browser-sync/browser-sync-client.2.13.0.js'><\/script>".replace("HOST", location.hostname));
//]]></script>
```

- 运行前先进行BrowerSync 的安装  http://www.browsersync.cn
```
npm install -g browser-sync

```

- 然后直接运行 就可以监控修改的文件 同步浏览器修改
```
browser-sync start --server --files "css/*.css"
```

浏览器打开页面:
```
http://localhost:3000/html/profile.html

或者打开 
http://10.0.1.106:3001
```

可用考拉工具进行`sass`的编译 地址: http://koala-app.com/index-zh.html
或者是用sass的命令行进行编译 http://www.w3cplus.com/sassguide/compile.html
```
 sass --watch jingoal.scss:../css/jingoal.css --style compact 

```

- [目录结构]

```
Jingoal/
├── sass/  sass文件目录
│    ├── base      项目中一些模板相关 如重置文件
│    ├── componts  小组件样式文件
│    ├── mixins    项目中关于Sass的工具 或者全局变量（比如排版本上的，配色方案等等）
│    └── pages     针对一些页面写特定的样式 后期增加页面或者其他页面
├── js/    js文件目录
├── fonts/ 字体图标文件
├── image/ 图片目录
├── css/   编译后的sass文件为css
├── doc/   文档或者工具目录
└── html/  所有的html页面存放目录
```


- 结构 

> 整合的时候 jg-tab-cons只用一个div进行内容的切换，这里注意下，但是前端页面展示还是三个DIV进行页面的展示

```
 <!--Tab 切换--> 
<div class="jg-tab">
    <div class="clearfix">
        <ul class="jg-tab-title">
            <li><a class="jg-title-tit active">Information</a></li>
            <li><a class="jg-title-tit">Settings</a></li>
            <li><a class="jg-title-tit">Team</a></li>
        </ul>
    </div>
    <div class="jg-tab-con">
        <div class="jg-tab-cons active"></div>
        <div class="jg-tab-cons"></div>
        <div class="jg-tab-cons"></div>
    </div>
</div>
```
 
> 注意: 常用的类名

- 子级 清浮动 需要在父级 加`.clearfix`  

- 组件的类型都 `jg-*` 开头的写法

- 类名 `.ui-hide`  隐藏元素    

- 类名 `.ui-show`  显示元素

- 类名 `.f12` `.f14` `.f18` `.f20` `.f22`  控制字体大小 常用来写在字体图标的class上

```
【按钮】
 
 // 确定按钮
 .jg-btn-success 
 
 // 取消按钮
 .jg-btn-cancel
 
  // 默认按钮
 .jg-btn-default
 
 .jg-btn 

 // 增加loading 效果
 .jg-loading 
 
 // loading 按钮 用于 下拉加载或者是提示 包含loading 文本提示
 .jg-btn-loading
 
 // 默认按钮都是96px
 // 如果要大按钮 200px  就加 .jg-big-btn 

 .jg-btn-disable类 用来禁止点击的状态 或者有个disabled 属性就行实现不能点击状态
 <button class="jg-btn" disabled>Cancel</button>

 
```

- 表单
```
   // 输错的文本红色提示    jg-error-tips
   // 文本提示(比如每个表单前面的文本说明 样式 )   jg-tips-default
   // 错误提示(红色边框)的类  jg-error  
   // 聚焦的样式 jg-focus
   // 默认表单的样式 jg-input(jg-input-default)   360px * 92px
   // 
```

- 开关按钮
```
 <label class="jg-switch"><input type="checkbox" checked><i></i></label>
 // checked 表示选中状态  没有就是不选中 
```

- css3 动画library
```
 引入 css3 动画库 https://daneden.github.io/animate.css/
```

- 组件弹出层 大致结构
```
<!-- 组件弹出层 -->
<!-- ui-hide 隐藏modal  -->
<!-- jg-modal-com 为通用的 去掉就是 类似通知 之类的弹窗 文本啥的都居中  -->
<div class="jg-modal jg-modal-com">
    <div class="jg-modal-mask"></div>
    <!-- animated bounceInDown 这两个类 animated是 必须写的 bounceInDown是动画效果(可用其他效果 参考animate.css) 需要JS控制出来消失 -->
    <div class="jg-modal-box animated bounceInDown">
        <!-- 主标题放进head-->
        <div class="jg-modal-thead">
            <h2 class="jg-modal-title">Invite Team Members</h2>
            <i class="jg-close icon-closei f14"></i>
        </div>
        
        <!-- 文本都放进body -->
        <div class="jg-modal-body">
            <h2 class="jg-modal-head">Are you sure you want to leave this team?</h2>
            <!-- 里面文本你都用p 标签 -->
            <!-- 默认文本都居中 考虑到如果特殊情况文字多的时候需要居左的 加个类名 .ui-align-left -->
            <p class="ui-align-left">A member of this will need to invite you if you want to rejoin this team, your workstreams and fileswill be kept safe if you join again,this will bot affect your membership in other teams</p>
            <p>这是增加一行居中文本的情况</p>
        </div>
        <!-- 按钮都放进footer -->
        <div class="jg-modal-footer">
            <!-- 按钮规则: jg-btn 代表实现一个按钮的功能 jg-big-btn 表示这个按钮是大的 jg-btn-blue 按钮颜色 -->
            <button disabled class="jg-btn jg-btn-gray">Cancel</button>
            <button class="jg-btn jg-big-btn jg-btn-blue">Yes, delete this team</button>
            <!--<button class="jg-btn jg-btn-blue">OK</button>-->
            <!--<button class="jg-btn jg-big-btn jg-btn-blue">OK</button>-->
        </div>
    </div>
</div>
```

- 表单 带有 `清除按钮`
```
<!-- 结构 -->
<div class="jg-input-close ui-margin-cen">
    <input type="text" class="jg-input-default">
    <i class="jg-close icon-closei f14"></i>
</div> 
```
