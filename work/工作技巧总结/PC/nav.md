### html

```
<div class="topics-colour-nav topics-nav-fixed">
            <ul class="topics-nav-list">
                <li class="active"><a href="#colour1">原理解析</a></li>
                <li><a href="#colour2">人体运用</a></li>
                <li><a href="#colour3">场景运用</a></li>
                <li><a href="#colour4">后期处理</a></li>
            </ul>
        </div>
```

css

```

```

### js

```
<script src="{{ asset('staticPS/js/plugins/navscroll/navscroll.js') }}"></script>
$(function() {
    // nav滚动效果实现    （疑问：1. 页面滚动时添加nav中的li自动添加active样式；2. 下面那两个方法是啥）
        // 指定nav起始位置，相对于layouts布局
        pageNavPosition('.topics-nav-fixed', 600);
        // ？？？
        $(".topics-nav-fixed").onePageNav();
        // 实现nav锚点效果，点击滚动至对应锚点位置，采用$("html,body").animate的API
        scrollTop('.colour2-item');
    });
        // 跳转至指定id
        function scrollTop(e) {
            $(e).on('click', function() {
                var index = $(this).attr("rel");
                var id = '#' + index;
                $("html,body").animate({
                    scrollTop: $(id).offset().top
                }, 800);
            });
        }
    });
```

