==图片放大效果==

===已有的实现===
 * jqzoom: 基于jQuery的图片放大功能, http://www.mind-projects.it/projects/jqzoom/
    - 实现了多种显示方式;
    - 图片预加载;
    - 提供n种配置参数, 方便设置, 也有些特效参数;

 * imagezoom: http://www.cnblogs.com/cloudgamer/archive/2010/04/01/ImageZoom.html
    - 实现多种显示方式;
    - 可设置放大系数;
    - 支持滑轮滚动缩放;

 * imageScaler: 基于Ext的, http://yiminghe.javaeye.com/blog/388872
    - 承玉实现的一款; 
    - 也有缩放功能, 支持拖拽, 移动;

 * AnythingZoomer: http://css-tricks.com/examples/AnythingZoomer/image.php
    - 功能比较简单, 只有跟随模式;

 * imagezoom:
    - 我的实现, 基于苏青代码, 重构成kissy组织方式;
    - 支持最一般的放大效果;
    - 缩放区域大小可设置;

===多种显示方式===
 . 最一般的:
    图片放大效果, 鼠标移到那里的一个特定范围内的图片被放大显示, 显示框在原图旁边;
    file: pics/Snap3.gif
    
 . 显示镜片(又称手柄模式):
    同上类似, 但在原图上显示出半透明的镜片效果, 指明被放大的区域是哪个;
    file: pics/Snap4.gif
    
 . 跟随模式:
    显示框跟随鼠标移动, 即被放大的图片显示在原图上方, 并以鼠标为轴心;
    如: AnythingZoomer
    file: pics/Snap2.gif
    
 . 反转模式:
    同第二种类似, 只是原图变成半透明, 镜片覆盖的区域清晰显示;
    file: pics/Snap1.gif


==其他考虑因素==
 . 放大系数
    小图到大图的放大系数;
    
 . 图片加载
    大图片一般都会很大, 可以考虑预加载. 可仿照jqzoom;
    如果大图没有加载完成时, 可直接使用原图;
    
 . 放大镜图标
    如淘宝商品页面: 默认有一个放大镜在小图右下角，提醒用户有放大的功能，用户引导性比较好。鼠标移至小图上方，放大镜消失。





== ImageZoom ==
===目录结构===
|--imagezoom.js 核心组件
|--imagezoom.css 测试页面样式, 其中包含一些imagezoom组件所需的样式
|--test.html 测试页面
\--pics 样例

===使用===
 . 示例
html{{{
<div id="page">
    <img id="smallimg" class="jqzoom" src="close1_small.jpg" />
</div>
}}}
js{{{
KISSY.ready(function(S) {
    var zm = S.ImageZoom("#smallimg", // 提供被放大图片选择器
                        {bigImageSrc:"close1_big.jpg"});
});
}}}

 . 构建出的DOM结构为
html{{{
    <div class="ks-imagezoom-container" style="height: 352px; margin-left: 320px;">
        <div class="ks-imagezoom-magnifier" data-ks-event-guid="1277113364450">
            <img src="close1_small.jpg" class="jqzoom" id="smallimg">
            <div class="ks-imagezoom-glass hidden" style="height: 100px; width: 100px; left: 0px; top: 210px;"></div>
            <div class="ks-imagezoom-icon"></div>
        </div>
        <div class="ks-imagezoom-viewer hidden" style="top: 20px; left: -300px; height: 310px; width: 310px;">
            <img src="close1_big.jpg">
        </div>
    </div>
}}}

 . 配置选项
js{{{
    bigImageSrc: '',    // 大图片路径, 为''时取原图路径
    offset: 10,         // 大图偏移量
    glassSize: [100, 100],      // 镜片高,宽度
    useZoomIcon: true,          // 是否需要zoomicon
    zType: 'default',           // 选择显示模式, 可选值: ['default', 'glass', 'follow']
    position: 'right',          // 大图显示位置, 可选值: ['top', 'right', 'bottom', 'left']
    preload: true               // 是否预加载
    timeout: 6000,              // 等待大图加载时间, 单位: ms
    bigImageSize: {height:900, width:900}     // 设定大图的高宽度, 当大图未加载完毕时取该值
    
}}}
 . 注意事项
    1. 跟随模式下生成的dom有点不同, 直接把ks-imagezoom-viewer这层放到ks-imagezoom-magnifier中;
    2. 关于显示区域宽高, 显示区域宽=大图宽度*镜片宽度/小图宽度;
    3. 延时设置, 当超过timeout时间之后, 图片仍未加载, 会给出提示, 如果之后图片加载成功会覆盖提示;
    4. 



