==ͼƬ�Ŵ�Ч��==

===���е�ʵ��===
 * jqzoom: ����jQuery��ͼƬ�Ŵ���, http://www.mind-projects.it/projects/jqzoom/
    - ʵ���˶�����ʾ��ʽ;
    - ͼƬԤ����;
    - �ṩn�����ò���, ��������, Ҳ��Щ��Ч����;

 * imagezoom: http://www.cnblogs.com/cloudgamer/archive/2010/04/01/ImageZoom.html
    - ʵ�ֶ�����ʾ��ʽ;
    - �����÷Ŵ�ϵ��;
    - ֧�ֻ��ֹ�������;

 * imageScaler: ����Ext��, http://yiminghe.javaeye.com/blog/388872
    - ����ʵ�ֵ�һ��; 
    - Ҳ�����Ź���, ֧����ק, �ƶ�;

 * AnythingZoomer: http://css-tricks.com/examples/AnythingZoomer/image.php
    - ���ܱȽϼ�, ֻ�и���ģʽ;

 * imagezoom:
    - �ҵ�ʵ��, �����������, �ع���kissy��֯��ʽ;
    - ֧����һ��ķŴ�Ч��;
    - ���������С������;

===������ʾ��ʽ===
 . ��һ���:
    ͼƬ�Ŵ�Ч��, ����Ƶ������һ���ض���Χ�ڵ�ͼƬ���Ŵ���ʾ, ��ʾ����ԭͼ�Ա�;
    file: pics/Snap3.gif
    
 . ��ʾ��Ƭ(�ֳ��ֱ�ģʽ):
    ͬ������, ����ԭͼ����ʾ����͸���ľ�ƬЧ��, ָ�����Ŵ���������ĸ�;
    file: pics/Snap4.gif
    
 . ����ģʽ:
    ��ʾ���������ƶ�, �����Ŵ��ͼƬ��ʾ��ԭͼ�Ϸ�, �������Ϊ����;
    ��: AnythingZoomer
    file: pics/Snap2.gif
    
 . ��תģʽ:
    ͬ�ڶ�������, ֻ��ԭͼ��ɰ�͸��, ��Ƭ���ǵ�����������ʾ;
    file: pics/Snap1.gif


==������������==
 . �Ŵ�ϵ��
    Сͼ����ͼ�ķŴ�ϵ��;
    
 . ͼƬ����
    ��ͼƬһ�㶼��ܴ�, ���Կ���Ԥ����. �ɷ���jqzoom;
    �����ͼû�м������ʱ, ��ֱ��ʹ��ԭͼ;
    
 . �Ŵ�ͼ��
    ���Ա���Ʒҳ��: Ĭ����һ���Ŵ���Сͼ���½ǣ������û��зŴ�Ĺ��ܣ��û������ԱȽϺá��������Сͼ�Ϸ����Ŵ���ʧ��





== ImageZoom ==
===Ŀ¼�ṹ===
|--imagezoom.js �������
|--imagezoom.css ����ҳ����ʽ, ���а���һЩimagezoom����������ʽ
|--test.html ����ҳ��
\--pics ����

===ʹ��===
 . ʾ��
html{{{
<div id="page">
    <img id="smallimg" class="jqzoom" src="close1_small.jpg" />
</div>
}}}
js{{{
KISSY.ready(function(S) {
    var zm = S.ImageZoom("#smallimg", // �ṩ���Ŵ�ͼƬѡ����
                        {bigImageSrc:"close1_big.jpg"});
});
}}}

 . ��������DOM�ṹΪ
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

 . ����ѡ��
js{{{
    bigImageSrc: '',    // ��ͼƬ·��, Ϊ''ʱȡԭͼ·��
    offset: 10,         // ��ͼƫ����
    glassSize: [100, 100],      // ��Ƭ��,����
    useZoomIcon: true,          // �Ƿ���Ҫzoomicon
    zType: 'default',           // ѡ����ʾģʽ, ��ѡֵ: ['default', 'glass', 'follow']
    position: 'right',          // ��ͼ��ʾλ��, ��ѡֵ: ['top', 'right', 'bottom', 'left']
    preload: true               // �Ƿ�Ԥ����
    timeout: 6000,              // �ȴ���ͼ����ʱ��, ��λ: ms
    bigImageSize: {height:900, width:900}     // �趨��ͼ�ĸ߿���, ����ͼδ�������ʱȡ��ֵ
    
}}}
 . ע������
    1. ����ģʽ�����ɵ�dom�е㲻ͬ, ֱ�Ӱ�ks-imagezoom-viewer���ŵ�ks-imagezoom-magnifier��;
    2. ������ʾ�������, ��ʾ�����=��ͼ����*��Ƭ����/Сͼ����;
    3. ��ʱ����, ������timeoutʱ��֮��, ͼƬ��δ����, �������ʾ, ���֮��ͼƬ���سɹ��Ḳ����ʾ;
    4. 


