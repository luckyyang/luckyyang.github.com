---
layout: post
title: "rails 程序中的布局"
date: 2014-12-24 22:31
comments: true
categories: rails
---

rails中的layout是指每个页面中都会出现的部分。比如说页面顶部的导航条（header）和页脚（footer），每个页面中都会出现，所以把它们的代码放到layout中最合适。

下面的笔记是读railsapps的[Rails Application Layout](http://railsapps.github.io/rails-default-application-layout.html)教程记录下来的：

- HTML5 Boilerplate从2010年开始推荐前端的一些“最佳实践”
- 可以用前端框架来配合rails使用：
   - Bootstrap
   - Foundation
- `stylesheet_link_tag`和`javascript_include_tag`从[Rails asset pipeline](http://guides.rubyonrails.org/asset_pipeline.html)中添加CSS stylesheets和Javascripts
- `data-turbolinks-track`属性添加对Rails [Turbolinks](https://github.com/rails/turbolinks/blob/master/README.md)的支持
- `csrf_meta_tags`元素是一个view helper，用于用户在表单中输入数据的时候，防止[跨站请求的伪造](https://en.wikipedia.org/wiki/Cross-site_request_forgery)（ cross-site request forgeries）
- `yield`这个关键字用来插入rails中view的内容。参考RailsGuides  [Layouts and Rendering in Rails](http://guides.rubyonrails.org/layouts_and_rendering.html#using-render)部分，解释了Rails如何将view和layout结合起来
- `$ rails generate layout:install simple --force`生成一个layout，`--force`参数用来替换当前的`app/views/layouts/application.html.erb`文件
- `viewport` metatag用来让页面在手机上显示的效果更好。设定一个viewport告诉浏览器如何让内容适应屏幕。apple的开发者文档中[如何配置viewport](http://developer.apple.com/library/safari/#documentation/AppleApplications/Reference/SafariWebContent/UsingtheViewport/UsingtheViewport.html)有详细的说明
- 如果你想调用外部的javascript来执行，可以在body中添加类来区分开每个页面，让javascript在指定的页面中执行：`<body class="<%= controller_name %> <%= action_name %>">`。具体可以参考railsapps上的[给Rails添加JavaScript](http://railsapps.github.io/rails-javascript-include-external.html)这篇文章
- html5元素
  - `<header> 用于branding或者导航`
  - `<main>`中的内容对于一个页面来说是这个页面独有的，因此就不包括导航，网站logo，页脚等。W3C建议使用ARIA role="main"属性给main元素添加残疾人的支持。
- flash message：rails提供的一套标准的惯例来显示警告（alert）和通知（notice），叫做flash message。这个名字来源于`flash memory`。具体可以参考[RailsGuides的文档](http://guides.rubyonrails.org/action_controller_overview.html#the-flash)
- `content_tag` view helper:
`<%= content_tag :div, msg, :class => "flash_#{name}" %>`(完)