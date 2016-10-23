# ajax

[参考资料](http://www.runoob.com/ajax/ajax-tutorial.html)

#### 什么是ajax？

AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。

#### 创建一个XMLHtmlRequest对象

所有现代浏览器均支持 XMLHttpRequest 对象（IE5 和 IE6 使用 ActiveXObject）。

  创建XMLHttpRequest对象的方法

  ```
  var xhr = new XMLHttpRequest();

  ```

  为了兼容 老浏览器 需要判断浏览器是否支持 XMLHttpRequest 来写出兼容性代码

  ```
  var xhr = null;
  if (window.XMLHttpRequest){
    xhr = new XMLHttpRequest() //浏览器支持 XMLHttpRequest对象 直接创建
  }else{
    xhr = new ActiveXObjce('Microsoft.XMLHTTP')
  }

  ```

#### 向服务器发送请求

  利用 XMLHttpRequest 对象的 `open()` 和 `cend()` 方法。

  | 方法            |      描述     |
  | :------------- | :------------- |
  |open(method,url,async) | method：请求的类型；GET 或 POST <br/> url：请求地址 <br /> async：true（异步）或 false（同步）|
  |  send(string)  | 将请求发送到服务器 <br /> <br /> &nbsp;string：仅用于 POST 请求 |

  - GET 请求

  ```
  xhr.open('GET','https://api.github.com/users/zhaozhuoboy','true') ;
  xhr.send();

  ```

  - POST请求

  > 如果需要像 HTML 表单那样 POST 数据，需要使用 setRequestHeader() 来添加 HTTP 头。然后在 send() 方法中规定发送的数据：

  ```

  xhr.open("POST","ajax_test.html",true);
  xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
  xhr.send("fname=Henry&lname=Ford");

  ```

#### 服务器的响应

XMLHttpRequest 对象的 responseText 或 responseXML 属性 保存着服务器响应的数据

#### onreadystatechange 事件

  **当 readyState 改变时，就会触发 onreadystatechange 事件**

  _readyState_ 属性存储着 XMLHtmlRequest 的状态，0-4 五种状态

  - 0: 请求未初始化
  - 1: 服务器连接已建立
  - 2: 请求已接收
  - 3: 请求处理中
  - 4: 请求已完成，且响应已就绪

  _status_ 的状态值： *200: "OK"  404: 未找到页面*

  当 readyState 等于 4 且状态为 200 时，表示响应已就绪

  ```
  //如果async = true   异步请求时候 就要在  onreadystatechange这个 方法触发的时候 进行下一步的操作
  xhr.onreadystatechange=function()
  {
  if (xhr.readyState==4 && xhr.status==200)
    {
    document.getElementById("myDiv").innerHTML=xhr.responseText;
    }
  }

  ```

  > 注意： onreadystatechange 事件被触发 5 次（0 - 4），对应着 readyState 的每个变化。


# json字符串与json对象的相互转换

实际操作中 请求的API 返回的数据 都是json对象格式，而 `xhr.responseText` 的值 却是字符串。

这就需要将json字符串转换成 json对象

#### Javascript支持的转换方式：

`eval('(' + jsonstr + ')');`

可以将json字符串转换成json对象,注意需要在json字符外包裹一对小括号
> 注：ie8(兼容模式),ie7和ie6也可以使用eval()将字符串转为JSON对象，但不推荐这些方式，
这种方式不安全eval会执行json串中的表达式。


浏览器支持的转换方式(Firefox，chrome，opera，safari，ie9，ie8)等浏览器：

`JSON.parse(jsonstr);` //可以将json字符串转换成json对象
`JSON.stringify(jsonobj);` //可以将json对象转换成json对符串

> 注：ie8(兼容模式),ie7和ie6没有JSON对象，推荐采用JSON官方的方式，引入json.js。
