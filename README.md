
###rem如何自适应，针对移动端
<p>页面引入一下JS</p>
<ul>
    <li>在html内最外层元素给max-width:640px,min-width:320px</li>
    <li>元素宽高都以rem为单位就会自动缩放</li>
    <li>字体大小一般0.2rem-0.34rem</li>
    <li>引入img标签时候该img必须float否则其与父元素有20px左右的margin-bottom</li>
    <li>参考来源: <a href="http://www.jianshu.com/p/b00cd3506782/comments/1599498">猛戳此处</a></li>
</ul>
<pre style="color:green">
        /**
         * Created by Administrator on 2016/6/2.
         */
        (function (doc, win) {
            var docEl = doc.documentElement,
                resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
                recalc = function () {
                    var clientWidth = docEl.clientWidth;
                    if (!clientWidth) return;
                    if(clientWidth>=640){
                        docEl.style.fontSize = '100px';
                    }else{
                        docEl.style.fontSize = 100 * (clientWidth / 640) + 'px';
                    }
                };
            if (!doc.addEventListener) return;
            win.addEventListener(resizeEvt, recalc, false);
            doc.addEventListener('DOMContentLoaded', recalc, false);
        })(document, window);
</pre>