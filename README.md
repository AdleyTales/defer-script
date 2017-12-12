## 异步加载script

#### 方案：

    正常情况,加载 script 标签，是同步的但是 script 标签，会阻塞加载，
    放在html页面的head标签，肯定会影响用户体验。加载页面时候，会出现
    一段时间的空白，当然，可以：

    1> 加一张 gif 或 动画 ，作为等待框，直至加载完毕，再隐藏等待框。

    2> 将script标签放到body的底部，不会影响dom和style的加载，提升用户体验。

    3> 异步加载 script 在 script标签加上defer属性，之后就是无阻塞请求文件。
    但是自己的业务逻辑的js代码，会依赖js库，就会报错，所以就要在script
    onload事件之后，执行自己的业务代码。


##### 写的一个进度条代码：
```js

    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <title></title>
        <link rel="stylesheet" href="css/mescroll.min.css">
        <style media="screen">
          div.fa{
            width: 1000px;
            height: 4px;
            border: 1px solid #ccc;
            margin: 30px auto;
          }
          div.ch {
            width: 0;
            height: 4px;
            background: #00f;
          }
        </style>
        <script type="text/javascript">
          var t1 = new Date().getTime();
          console.log(t1);
        </script>

        <script defer onload="fn()"  src="https://cdn.bootcss.com/vue/2.5.9/vue.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/echarts/3.8.5/echarts.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/Chart.js/2.7.1/Chart.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/vue/2.5.9/vue.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/echarts/3.8.5/echarts.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/Chart.js/2.7.1/Chart.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/vue/2.5.9/vue.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/echarts/3.8.5/echarts.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/Chart.js/2.7.1/Chart.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/vue/2.5.9/vue.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/echarts/3.8.5/echarts.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/Chart.js/2.7.1/Chart.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/vue/2.5.9/vue.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/echarts/3.8.5/echarts.js"></script>
        <script defer onload="fn()"  src="https://cdn.bootcss.com/Chart.js/2.7.1/Chart.js"></script>

      </head>
      <body>
        <h1></h1>
        <div class="app">
            {{msg}}
        </div>

        <div class="fa">
          <div class="ch">

          </div>
        </div>

        <script type="text/javascript">
          var t2 = new Date().getTime();
          console.log(t2);
          console.log('用时：',t2-t1);
          document.querySelector('h1').innerHTML = (t2-t1) + 'ms';
          document.querySelector('h1').style.color = '#f00';
        </script>

        <script type="text/javascript">

          var num = null;
          var g = 20;
          function fn(){
            // console.log(Vue);
            // var el = new Vue({
            //   el:'.app',
            //   data: {
            //     msg: 'jdsfljksld'
            //   }
            // })

            num += 100/g;

            document.getElementsByClassName('ch')[0].style.width = 10 * num + 'px';

          }

  </script>

  </body>
</html>


```
