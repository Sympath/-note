### 判断用户状态

```
@guest
        @php $login = 0; @endphp
@else
        @php $login = 1; @endphp
@endguest

Number("@php echo $login; @endphp"),
未登录重定向且设置登录后返回页面
sessionStorage.setItem('recordUrl', location.href);
window.location.href = "/register";
```

### 注意点

- 存在localStorage中的数据必须是string

