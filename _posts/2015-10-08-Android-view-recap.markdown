---
title:  "Android view components recap"
date:   2015-10-08 10:18:00
---


#TextView
这个可以说是Android中最简单
的一个控件了。该控件主要用来显示一段文字。
其中控件的显示设置也很简单，这里简单说一下重要的几个，控件的id，layout_weigth（宽度），layout_height（高度），text（显示文字内容）等都是比较常用和简单的设置，不在详细描述。

###gravity
定义控件中文字的对齐方式，可选值有center，top， bottom， letf， right等，可以用“|”来制定多个值。

###textSize
定义控件中文字的大小，一般都采用sp。

#Button
这个是大家在熟悉不过的了，初学者在学习的时候都是最先使用Button进行练习。
他控件的显示设置也很简单，如TextView一样包括：id，宽，高，名称（也就是显示的文字）等的设置。

Button 还有一种使用就是使用监听器，实现点击事件。首先在Activity的onCreate方法中添加如下代码：
方式一：通过匿名内部类的方法来实现监听。

{% highlight java %}
Button btnSecond = (Button)findViewById(R.id.btnSecond);
btnSecond.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intentSecond = new Intent(MainActivity.this,MainActivity.class);
                startActivity(intentSecond);
            }
        });
{% endhighlight %}
Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh].

[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
