# 解决 vue-cli + element-ui 在 npm run build 时与 UglifyJs 冲突的问题
## 问题
我在最近软工课程的大作业：给贵系写一个体育赛事报名系统中，选用了 Vue  + element-ui 作为前端，Django 作为后端的解决方案。
由于几周来演示过程中普通用户页面一直用的是前端的开发环境（方便快捷），所以很久没有执行过 build 操作了。
结果今天展示前临时想要 build 一下， 发现 npm 报错了，错误如下：
~~~
ERROR in static/js/vendor.f1c68aa2d5e85847d30e.js from UglifyJs
Unexpected token name «i», expected punc «;» [./node_modules/element-ui/src/utils/merge.js:2,0][static/js/vendor.f1c68aa2d5e85847d30e.js:17064,11]
Build failed with errors.
~~~
就 error massage 来看，应该是 `UglifyJs` 这个 Module 和 `element-ui` 存在冲突。遂 google 之。
## 尝试1
结果首先在 UglifyJs 的 github issues #78 找到了这样一个解决方案：
由于 UglifyJs 只支持 ES5 而 element-ui 可能引入了一部分 ES6 的写法，所以导致 webpack 打包失败。
issue 里最后给出的解决方案是用 beta 版本的Uglify-es 来代替 UglifyJs（Beta 版本引入了对 ES2015+）的支持。需要在前端工作目录下用执行命令 npm i -D uglifyjs-webpack-plugin@beta。
不过在尝试过后，发现 build error 的问题依然没有解决。
## 尝试2
在深入查找问题所在后，决定用 bable 来解析 element-ui。 
要完成此操作只需要修改前端文件夹下的build/webpack.base.conf.js 文件即可，修改如下：
修改前
{% highlight json %}
module: {
rules: [
{
test: /\.js$/,
loader: 'babel-loader',//注意elementUI的源码使用ES6需要解析
include: [resolve('src'), resolve('test'),resolve('/node_modules/element-ui/src'),resolve('/node_modules/element-ui/packages')]
},
{% endhighlight %}
修改后
{% highlight json%}
module: {
rules: [
{
test: /\.js$/,
loader: 'babel-loader',//注意elementUI的源码使用ES6需要解析
include: [resolve('src'), resolve('test'),resolve('/node_modules/element-ui/src'),resolve('/node_modules/element-ui/packages')]
},
{% endhighlight %}
相当于将 element-ui 加入需要 babel 解析的包中。

之后再次执行 npm run build， build 成功。
