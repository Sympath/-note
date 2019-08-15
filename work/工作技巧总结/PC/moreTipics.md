### html

```
 <section class="colour-c8">
            <div class="colour-h2">
                <h2 class="animated fadeInUp"><img src="/staticPS/imgs/c8-title.png" alt="更多精彩专题"><em></em></h2>
                <h3 class="animated fadeInUp">MORE TOPICS</h3>
            </div>
            <div class="container topics-more">
                @include('page.topicsMoreLS')
            </div>
        </section>
```

### css

```

```

### js

```
 $(function() {
    // 加载更多轮播实现
         var topicsMore = new Swiper('.topics-more .swiper-container', {
            navigation: {
                nextEl: '.topics-more-page.next',
                prevEl: '.topics-more-page.prev',
            },
            preventClicks: false,
            slidesPerView: 'auto',
            spaceBetween: 20,
            on: {
                init: function() {
                    this.removeSlide(11);
                }
            }
        });
```

