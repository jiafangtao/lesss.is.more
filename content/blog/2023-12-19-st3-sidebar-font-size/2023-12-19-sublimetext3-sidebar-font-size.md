---
layout: post
title: "如何修改Sublime Text 3中侧边栏字体大小"
date: 2023-12-19 11:21:00+08:00
authors:
- brucejia
tags: 
  - sublime
  - tips
description: "最爱的编辑器Sublime Text 3的侧边栏字体非常小，怎么破？"
categories: "小技巧"

---


自从老花眼之后看比较小的字体都非常吃力，翩翩最爱的编辑器Sublime Text 3的缺省字体非常小。对于主编辑区域来说调整字体非常easy,按住**Control键**滚动鼠标中键就可以了。但是对于**侧边栏** (sidebar)怎么办？

求助*谷歌*，翻了几个帖子之后还是找到了这个最靠谱的方法。

链接：[https://forum.sublimetext.com/t/increase-side-of-the-ui-menus-folders-etc/46704/3](https://forum.sublimetext.com/t/increase-side-of-the-ui-menus-folders-etc/46704/3)

具体步骤如下：

1. 通过`Command Palette` 输入命令  `Install Package` 安装`PackageDev`包 
2. 运行`PackageDev: Edit Current Theme` 注意选择你当前活动的主题。例如我输入这个命令时看到的有`dark_theme`和`light_theme`而`light_theme`是活动的（`Active`）。


```
{
    // http://www.sublimetext.com/docs/3/themes.html
    "variables": {
        "font_face": "system",
        "font_size": 16,
    },
    "rules": [

        // Label Controls
        {
            "class": "label_control",
            "font.face": "var(font_face)",
            "font.size": "var(font_size)",
        },

        // Quick Panels
        {
            "class": "quick_panel_label",
            "font.face": "var(font_face)"
            "font.size": "var(font_size)",
        },

        // Sidebar Header
        {
            "class": "sidebar_heading",
            "font.face": "var(font_face)",
            "font.size": "var(font_size)",
        },

        // Sidebar Label
        {
            "class": "sidebar_label",
            "font.face": "var(font_face)",
            "font.size": "var(font_size)",
        },

        // Tab Label
        {
            "class": "tab_label",
            "font.face": "var(font_face)",
            "font.size": "var(font_size)",
        },

        // Tooltip Control
        {
            "class": "tool_tip_label_control",
            "font.face": "var(font_face)",
            "font.size": "var(font_size)",
        },      
    ]
}

```

根据自己需要修改变量 `font_size` 的数值即可，这个修改是立刻生效的不需要重启Sublime Text3。另外注意这个修改了除sidebar header和label之前的其他元素的字体大小，如果你不需要修改也可以删掉或者注释掉。

