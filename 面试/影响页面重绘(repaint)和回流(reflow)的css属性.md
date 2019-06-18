# repaint(重绘)与reflow(重排)
* repaint:针对某一个DOM进行的重绘
* reflow:针对的是整个页面的重排  
性能消耗reflow大于repaint

# 如何触发
* repaint:不涉及任何DOM元素的排版的变动的为repaint,例如color/text-align等属性的变动
* reflow:例如元素的长、宽、行高等style的变动，都会触发reflow；另外，DOM元素的添加、修改(内容)、删除、浏览器resize、滚动页面

# 如何避免
其实避免是不可能的，因为如果页面没有交互，就是一个古老的静态网站，在目前而言就是失败的作品；所以我们这里提到的是尽量的避免：

1. 设置动画元素position为fixed或者absolute：由于该属性会让当前元素从DOM流中独立出来，因此受影响的只有当前元素，元素只会执行repaint重绘
2. 避免使用table进行布局，table的每个元素的大小会随内容的变动而改变，从而导致整个table进行重新计算，造成大幅度的repaint和reflow
3. 由于display:none元素不在渲染树中，对隐藏的元素操作不会引起其他元素的重拍，所以可以利用这个特性做一些操作(将元素的display设置为”none”，完成修改后再把display修改为原来的值)
4. 如果需要创建多个DOM节点，可以使用DocumentFragment创建完后一次性的加入document  
> function appendEveryTime(){
    for( var i = 5000; i--; ){
        var n = document.createElement('div');
        n.innerHTML = 'node ' + i;
        document.body.appendChild(n);/*每次创建的新节点都append到文档*/
    }
}

> function appendLast(){
     var frag = document.createDocumentFragment();
     for( var i = 5000; i--; ){
         var n = document.createElement('div');
         n.innerHTML = 'node ' + i;
         frag.appendChild(n);/*每次创建的节点先放入DocumentFragment中*/
     }
     document.body.appendChild(frag);
}

5. 样式方面，尽量集中修改样式(尽量少修改元素style上的属性、尽量通过className修改样式、js通过cssText属性来设置样式值)