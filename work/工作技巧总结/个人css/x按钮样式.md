html

```
   <div class="close"></div>
```

css

```
.close {
    position: absolute;
    width:0.706667rem;
    height:0.706667rem;
    border:1px solid rgba(255,255,255,1);
    border-radius:50%;
    background-color: #A0A0A0;
    left: 50%;
    transform: translateX(-50%);
    bottom: -1.16rem;
  }
  .close:before, .close:after {
    position: absolute;
    left: 50%;
    top: 50%;
    content: ' ';
    height: 0.426667rem;
    width: 0.026667rem;
    background-color: #fff;
  }
  .close:before {
    transform:  translate(-50%,-50%) rotate(45deg);
  }
  .close:after {
    transform:  translate(-50%,-50%) rotate(-45deg);
}
```

