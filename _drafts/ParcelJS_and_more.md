# ParcelJS

一个零配置的前端打包工具，跟其他工具的差别是不需要配置，直接上手。

Internals:

支持ES6模块。对于web前端vanilla JS，parcel生成一个parcelRequire函数挂载在window对象上。
同时它也支持CommonJS环境和AMD requireJS. 见下面ParcelJS生成的代码。

```
    // CommonJS
    if (typeof exports === "object" && typeof module !== "undefined") {
      module.exports = mainExports;

    // RequireJS
    } else if (typeof define === "function" && define.amd) {
     define(function () {
       return mainExports;
     });

    // <script>
    } else if (globalName) {
      this[globalName] = mainExports;
    }
```

我最近几天在web_programming项目里边试了下简单的用法。希望能在nc项目里边实战，积累经验。
如果parcelJS功能足够了，就用它了。

# uglifyjs

uglifyjs是另一个在试验的小工具，简单易用。需要跟CI集成一下，跟parceljs, gulp怎么集成还需要进一步研究。
