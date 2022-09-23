---
layout: default
title: bootstrap
description: bootstrap frontend
date: 2022-9-21 21:10:00 +0900
categories: [Web]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Quick Start

```html
<head>
    ...
    <!-- development -->
    <link rel="stylesheet" href="static/plugins/bootstrap-3.4.1/css/bootstrap.css">
    <!-- production -->
    <link rel="stylesheet" href="static/plugins/bootstrap-3.4.1/css/bootstrap.min.css">

    <style>
        .navbar{
            border-radius: 0;
        }
    </style>
</head>
<body>
    <!-- button -->
    <input type="button" value="enter" class="btn btn-primary"/>
    <!-- col-xs -->
    <div class="col-xs-offset-2 col-xs-2" style="color:red;">1</div>
    <div class="col-xs-2" style="color:green;">2</div>
    <!-- col-sm col-md col-lg -->
</body>
```