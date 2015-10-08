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

方式二：通过实现接口的方法来实现监听。
{% highlight java %}
public class MainActivity extends BaseActivity implements View.OnClickListener {
    private Button btnSecond;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        Log.d("Activity", this.toString());
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        btnSecond = (Button) findViewById(R.id.btnSecond);
        btnSecond.setOnClickListener(this);
    }
    @Override
    public void onClick(View view) {
        switch (view.getId()){
            case R.id.btnSecond:
                Intent intentSecond = new Intent(MainActivity.this,SecondActivity.class);
                startActivity(intentSecond);
                break;
            default:
                break;
        }
    }
}
{% endhighlight %}

#EditText
EditText是应用和用户进行交互的一个重要控件，用户在其中输入信息，EditText对信息进行处理传输。
他控件的显示设置也很简单，如TextView一样包括：id，宽，高，名称（也就是显示的文字）等的设置。

###hint
这个是EditText一个非常人性化的属性，我们经常会看到有好多输入框在输入前都会显示一些信息，当用户在进行输入的时候，信息就会消失。这个就是通过该属性进行实现的。

在布局文件中添加:
{% highlight xml%}
android:hint="Type something here"
{% endhighlight xml%}

![EditText](/assets/images/edittext.jpg)

###maxLines
EditText如果设置他的宽是“wrap_parent”，则随着输入内容的增多，输入框会被拉长，如果超过一行，会自动换行显示，显示的是全部内容。但是这样就有了一个弊端，如果我们输入的内容过多，输入框控件会占据我们屏幕的大部分空间并且会非常的丑，这时我们可以通过maxLines属性设置显示的最大行数。

###属性添加前：

![MaxLines](/assets/images/maxlines.gif)

###在xml布局文件添加android:maxLines="2"后：
![MaxLines](/assets/images/maxlines2.gif)

#ImageView

ImageView是用来在界面上展示图片的一个控件。它可以让我们的界面变的丰富多彩。
他控件的显示设置也很简单，如TextView一样包括：id，宽，高，名称（也就是显示的文字）等的设置。

{% highlight xml%}
<ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@mipmap/we_it"/>
{% endhighlight xml%}

结果：![ImageView](/assets/images/imageview.jpg)
#ProgressBar

有时候我们的应用程序正在加载一下数据，这是后我们就可以用ProgressBar控件来设置进度条。
他控件的显示设置也很简单，如TextView一样包括：id，宽，高，名称（也就是显示的文字）等的设置。
###style
默认情况下是圆形进度条，如果要更改样式，可以通过该属性进行修改。

###visibility
有时候数据加载完成后进度条就会消失，那么我们如何让进度条消失呢？我们可以通过visibility进行修改，该属性有三个值，分别是：visible(可见)， invisible(不可见)， gone(消失)。相应的程序应该在java代码中实现，这里不再详述。
#AlterDialog
该控件是弹出一个对话框，该对话框置于所有界面元素之上，屏蔽掉其他控件的交互能力。

#ProgressDialog
该控件是弹出一个对话框，该对话框置于所有界面元素之上，屏蔽掉其他控件的交互能力。与AlterDialog功能相似，但是不同的是ProgressDialog控件显示一个进度条，用于表示该操作比较耗时，请耐心等待。
