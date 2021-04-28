---
title: CSS盒子水平垂直居中
date: 2021-04-28 11:23:11
categories:
- 前端
tags:
- CSS
---

# 四种方式

第一种：采用绝对定位，使用margin-top: 负的盒子一般高度和margin-left: 负的盒子一半宽度（已知盒子宽高）

第二种：采用绝对定位，使用transform平移方式

第三种：采用绝对定位，上下左右为0，margin: auto

第四种：采用flex布局，justify-content: center和align-items: center

<!-- more -->

```html
<!DOCTYPE html>
<html lang="zh_CN">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>盒子水平垂直居中</title>
    <style>
        /* 第一种方式：margin-top和margin-left */
        .box1 {
            position: relative;
            width: 200px;
            height: 200px;
            margin-bottom: 20px;
            background-color: pink;
        }

        .box2 {
            position: absolute;
            top: 50%;
            left: 50%;
            width: 100px;
            height: 100px;
            margin-top: -50px;
            margin-left: -50px;
            background-color: blue;
        }

        /* 第二种方式：transform平移 */
        .box3 {
            position: relative;
            width: 200px;
            height: 200px;
            margin-bottom: 20px;
            background-color: pink;
        }

        .box4 {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 100px;
            height: 100px;
            background-color: blue;
        }

        /* 第三种方式：绝对定位上下左右设为0，margin：auto */
        .box5 {
            position: relative;
            width: 200px;
            height: 200px;
            margin-bottom: 20px;
            background-color: pink;
        }

        .box6 {
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            left: 0;
            width: 100px;
            height: 100px;
            margin: auto;
            background-color: blue;
        }

        /* 第四种方式：flex布局，justify-content：center和align-items：center */
        .box7 {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 200px;
            height: 200px;
            background-color: pink;
        }

        .box8 {
            width: 100px;
            height: 100px;
            background-color: blue;
        }
    </style>
</head>

<body>
    <!-- 第一种方式：知道盒子的具体宽高，使用margin-left和margin-top -->
    <div class="box1">
        <div class="box2"></div>
    </div>

    <!-- 第二种方式：使用CSS移动动画transform -->
    <div class="box3">
        <div class="box4"></div>
    </div>

    <!-- 第三种方式：使用绝对定位并设置top、right、bottom和left都为0，后使用margin：auto -->
    <div class="box5">
        <div class="box6"></div>
    </div>

    <!-- 第四种方式：使用flex布局 -->
    <div class="box7">
        <div class="box8"></div>
    </div>
</body>

</html>
```