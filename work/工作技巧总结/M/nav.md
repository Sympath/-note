### html

```
<ul class="colour-nav clearfix">
            <li><span class="colour2-item" rel="colour1">软件入门</span></li>
            <li><span class="colour2-item" rel="colour2">绘画基础</span></li>
            <li><span class="colour2-item" rel="colour3">进阶学习</span></li>
            <li><span class="colour2-item" rel="colour4">大触分享</span></li>
        </ul>
          
```

### css

```

.colour-nav {
    position: fixed;
    bottom: 0;
    z-index: 10;
    width: 10rem;
    background-color: #f5f5f5;
    -ms-box-shadow: 0 0 .066667rem rgba(29, 36, 117, .15);
    -o-box-shadow: 0 0 .066667rem rgba(29, 36, 117, .15);
    -webkit-box-shadow: 0 0 .066667rem rgba(29, 36, 117, .15);
    box-shadow: 0 0 .066667rem rgba(29, 36, 117, .15)
}

.topics-wrap .colour-nav li {
    float: left;
    width: 25%;
    text-align: center
}

.topics-wrap .colour-nav li.active .colour2-item,
.topics-wrap .colour-nav li:hover .colour2-item {
    background-color: #CB75FF;
    color: #fff
}

.topics-wrap .colour-nav .colour2-item {
    display: block;
    color:rgba(102,102,102,1);
    font-size: .32rem;
    line-height: 1.08rem;
    cursor: pointer
}
```

### js

```
 function scrollTopClass(e) {
      $(e).on('click', function() {
      var index = $(this).attr("rel");
      var id = '#' + index;
      $("html,body").animate({
        scrollTop: $(id).offset().top - 60
      }, 800);
      $(this).parent().addClass('active');
      $(this).parent().siblings().removeClass('active');
    });     
  }
  scrollTopClass(".colour2-item");
```

### tips

```
1. 在每个模块上加上.colour2-item上rel值对应的id
2. 注意js要放到onload中
3. 别忘记看类名，最外层需要一个类topics-wrap
```

