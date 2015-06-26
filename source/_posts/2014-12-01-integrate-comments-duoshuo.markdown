---
layout: post
title: "集成‘多说’评论"
date: 2014-12-01 16:48:23 +0800
comments: true
categories:
---

##首先申请多说评论，官网：http://duoshuo.com/ 添加站点获取shortname

###集成步骤：

1、在 _config.yml 中添加
``` ruby
# duoshuo comments
duoshuo_comments: true
duoshuo_short_name: yourname
```
<!-- more -->
2、在 source/_layouts/post.html 中的 disqus代码段：
``` ruby
{% if site.disqus_short_name and page.comments == true %}
  <section>
    <h1>Comments</h1>
    <div id="disqus_thread" aria-live="polite">{% include post/disqus_thread.html %}</div>
  </section>
{% endif %}
```

下方添加 多说评论 模块
``` ruby
{% if site.duoshuo_short_name and site.duoshuo_comments == true and page.comments == true %}
  <section>
    <h1>Comments</h1>
    <div id="comments" aria-live="polite">{% raw %}{% include post/duoshuo.html %}{% endraw %}</div>
  </section>
{% endif %}
```
3、创建duoshuo.html，路径：source/_includes/post/duoshuo.html
``` html
<!-- Duoshuo Comment BEGIN -->
<div class="ds-thread" data-title="{% if site.titlecase %}{{ page.title | titlecase }}{% else %}{{ page.title }}{% endif %}"></div>
<script type="text/javascript">
  var duoshuoQuery = {short_name:"{{ site.duoshuo_short_name }}"};
  (function() {
    var ds = document.createElement('script');
    ds.type = 'text/javascript';ds.async = true;
    ds.src = 'http://static.duoshuo.com/embed.js';
    ds.charset = 'UTF-8';
    (document.getElementsByTagName('head')[0] 
    || document.getElementsByTagName('body')[0]).appendChild(ds);
  })();
</script>
<!-- Duoshuo Comment END -->
```
4、修改 _includes/article.html 文件，在代码段：
``` ruby
{% if site.disqus_short_name and page.comments != false and post.comments != false and site.disqus_show_comment_count == true %}
| <a href="{% raw %}{% if index %}{{ root_url }}{{ post.url }}{% endif %}{% endraw %}#disqus_thread">Comments</a>
{% endif %}
```		
下方添加如下代码：
``` ruby
{% if site.duoshuo_short_name and page.comments != false and post.comments != false and site.duoshuo_comments == true %}
| <a href="{% raw %}{% if index %}{{ root_url }}{{ post.url }}{% endif %}{% endraw %}#comments">Comments</a>
{% endif %}
```