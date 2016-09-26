##1. dart语言特性中的循环语句定义和操作方法    
###FOR语句
```
main() {  var callbacks = []; 
         for (var i = 0; i < 2; i++) {  
              callbacks.add(() => print(i)); 
            }
         callbacks.forEach((c) => c());  
        }
```
```
for (var object in flybyObjects) {
  print(object);
}

for (int month = 1; month <= 12; month++) {
  print(month);
}
```
###while和do while循环与javascript中一样，break,continue中也一样。
```
while (!isDone()) {
  doSomething();
}
```
```
do {
  printLine();
} while (!atEndOfPage());
```
###IF判断语句
```
if (year >= 2001) {
  print('21st century');
} else if (year >= 1901) {
  print('20th century');
}
```
###break,continue语句
####使用break中断循环
```
while (true) {
  if (shutDownRequested()) break;
  processIncomingRequests();
}
```
####使用continue跳到下一个循环
```
for (int i = 0; i < candidates.length; i++) {
  var candidate = candidates[i];
  if (candidate.yearsExperience < 5) {
    continue;
  }
  candidate.interview();
}
```
###switch使用==来判断对象是否相等。
```
var command = 'OPEN';
switch (command) {
  case 'CLOSED':
    executeClosed();
    break;
  case 'PENDING':
    executePending();
    break;
  case 'APPROVED':
    executeApproved();
    break;
  case 'DENIED':
    executeDenied();
    break;
  case 'OPEN':
    executeOpen();
    break;
  default:
    executeUnknown();
}
```
####也支持空CASE的字句
```
var command = 'CLOSED';
switch (command) {
  case 'CLOSED': // Empty case falls through.
  case 'NOW_CLOSED':
    // Runs for both CLOSED and NOW_CLOSED.
    executeNowClosed();
    break;
}
```
####也支持continue陈述和标签
```
var command = 'CLOSED';
switch (command) {
  case 'CLOSED':
    executeClosed();
    continue nowClosed;
    // Continues executing at the nowClosed label.

nowClosed:
  case 'NOW_CLOSED':
    // Runs for both CLOSED and NOW_CLOSED.
    executeNowClosed();
    break;
}
```
##2. dart字符串的定义和操作方法
###(1).直接定义  var s1 = 'Single quotes work well for string literals.';
```
    var s2 = "Double quotes work just as well.";
```
###(2).也可以利用${expression}插入到，前提是expression是个标识符
```
var s = 'string interpolation';
assert('Dart has $s, which is very handy.' ==  'Dart has string interpolation, ' + 'which is very handy.');
```
###(3).可以通过邻近的字符串或"+"链接字符串  
```
var s1 = 'String ' 'concatenation'  " works even over line breaks.";
assert(s1 == 'String concatenation works even over '  'line breaks.');
var s2 = 'The + operator '   + 'works, as well.';
assert(s2 == 'The + operator works, as well.');
```
###(4).另一个创造多行的字符串可以采用多次引用单个标记符
```
          var s1 = '''
          You can create
          multi-line strings like this one.
          ''';
```
###(5).You can create a “raw” string by prefixing it with r:
```
var s = r"In a raw string, even \n isn't special.";
```
####(6).// These work in a const string.
```
 const aConstNum = 0;
 const aConstBool = true;
 const aConstString = 'a constant string';
```
###(7).//These do NOT work in a const string.
```
          var aNum = 0;
          var aBool = true;
          var aString = 'a string';
          const aConstList = const [1, 2, 3];
```
###(8).其他类型的变量
```
var name = 'Voyager I';
var year = 1977;
var antennaDiameter = 3.7;
var flybyObjects = ['Jupiter', 'Saturn', 'Uranus', 'Neptune'];
var image = {
  'tags': ['saturn'],
  'url': '//path/to/saturn.jpg'
};
```
##3. dart函数定义和使用方法
一个简单的能够运行的函数:
```
 bool isNoble(int atomicNumber) {
            return _nobleGases[atomicNumber] != null;
                                }//参数比较齐全，以及确定类型
 isNoble(atomicNumber) {
                  return _nobleGases[atomicNumber] != null;
                                }//缺少类型bool
 bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;//速成语句
```            
##4. dart中数组定义和使用方法
###list also knowed arrays;定义方法和c语言或是javascript一样，性质也是类似的
```        
         var list = [1, 2, 3];
         assert(list.length == 3);
         assert(list[1] == 2);
         var constantList = const [1, 2, 3];
```
##5.dart中列表定义和使用方法

###列表的定义

数组在Dart中数组也叫列表**list**.

下面是一个最简单的例子：
```
var list = [1, 2, 3];
```
列表使用从0开始索引的方式，0是第一个元素，列表长度-1是最后一个元素。
```
var list = [1, 2, 3];
assert(list.length == 3);
assert(list[1] == 2);

list[1] = 1;
assert(list[1] == 1);
```
###列表的使用方法
```
var gifts = {                      
// Keys       Values
  "first"  : "partridge",
  "second" : "turtledoves",
  "fifth"  : "golden rings"};

gifts["third"] = "apple"; //添加一个元素
```

##6.dart中 Map定义和使用方法

###map的定义

**map**表示一种映射，是“键”和“值”之间的联系。**map** 的字面量语法要求 key 是必须字符串，但如果是用构造函数创建的，则任何对象都可以是 key。
下面是一个案例：
```
var map = {
  'one': 1,
  'two': 2}; 
  // 或者 new Map(); 
assert(map['one'] == 1);
map['four'] = 4;
assert(map.length == 3);
```
也可以通过地图建造器制作同样的对象
```
var gifts = new Map();
gifts['first'] = 'partridge';
gifts['second'] = 'turtledoves';
gifts['fifth'] = 'golden rings';

var nobleGases = new Map();
nobleGases[2] = 'helium';
nobleGases[10] = 'neon';
nobleGases[18] = 'argon';
```
##7. querySelector（）函数的详细API解释
 ``` Element querySelector(String selectors) ```
 该函数的作用是寻找第一个符合selectors的当前document文档的子级元素
###Selectors的写法
 querySelector方法的参数selectors是一个css查询字符串，也就是类似于jquery的查询字符串
``` 
 var element1 = document.querySelector('.className');
//获取第一个class属性为className的元素
 var element2 = document.querySelector('#id'); 
 //获取第一个id属性叫做id的元素
var lioful = document.querySelector("ul li");
 //获取第一个ul元素下的第一个li元素
 //如果想要获得所有li元素可以调用querySelectorAll方法
 var lisoful = querySelectorAll("ul li");
 //返回的是一个ElementList对象，用法类似于HashMap
```
 在只有一个document文档的前提下，直接调用querySelector函数相当于使用document.querySelector
##8. 详细解释dart如何操作html的文档
<small>本页内容来自于<a href="https://api.dartlang.org/stable/1.19.1/dart-html/Element-class.html">Element类</a></small>
###1.获取DOM元素的方法:
 >__querySelector__: 获取符合查询条件的第一个DOM对象<br />
>__querySelectorAll__: 获取所有符合查询条件的DOM对象
###2.操作DOM元素属性与样式
####Element类有一个attributes属性和setAttribute方法
 >attributes → Map < String,  String \>
>All attributes on this element.   \( *read / write* \)
**比如说获取一个input元素的value** <br />
```
 var val = querySelector("input").attributes["value"];
```
当然element自己也有许多属性去获得该元素的信息

**比如说获得body元素可视区域的宽度** <br />
```var width = querySelector("body").clientWidth;```
####获取元素实际的样式
 >getComputedStyle([String pseudoElement ]) 
 @return CssStyleDeclaration
 <small>我们得到的是CssStyleDeclaration对象，需要在调用》CssStyleDeclaration方法才能获得css的值</small>
**比如说获取body元素的实际高度**
``` 
querySelector("body").getComputedStyle().getPropertyValue("height");
//返回字符串的格式是680px 数值+单位 
```
###3.为元素绑定事件

在Element类中on开头的属性都是我们可以用来绑定事件的属性
*例如以下的onclick属性*
>onClick → ElementStream<MouseEvent>
>Stream of click events handled by this Element.
<small>read-only</small>

**我们为一个input元素绑定一个点击时内容变为success的事件**

``` 
var input = querySelector("input");
input.onClick.listen((e){
   input.setAttribute("value","success");
     e.stopPropagation();
  }); 
```
 
<small>onClick是一个ElementStream对象有一个listen方法来设置click事件的回调函数</small>

##9. dart web app 应用程序组织结构的解释部分
 <small>以下是dart web app项目目录结构</small>
 >+web
 &emsp;+packages 
 &emsp;+dart
 &emsp;+style
 &emsp; index.html

<p>web目录是整个web程序的根目录，index.html就是我们的入口文件，style目录中存放css样式文件，dart目录中存放的是dart文件，而packages目录中存放的是dart语言的libraries，比如说我们希望使用dart:html库，那么就是加载了packages目录下的该库文件。</p>
 <small>.packages文件描述了库与文件路径的对应关系</small>
 
##10. dart可用的各种工具的解释部分
 #IDEs
 <p>dart语言的插件已经被许多常用的IDE （像webstorm等）所支持; </p>
 <p>当然也可以为一些文本编辑器（像vim、sublimetext等）安装dart的插件</p>
###SDKs
<table>
<thead><tr><td>用途</td><td>sdk</td></tr></thead>
<tbody><tr>
<td>web app(移动端的web页面)、作为脚本或服务器</td>
<td>dart</td>
</tr><tr>
<td>移动端原生app</td>
<td>Flutter</td>
</tr></tbody>
</table>
###命令行工具
####pub 包管理工具
 >管理Dart的包，用于安装，使用和分享Dart库，支持Dart插件的IDEs对pub都有支持；
####静态分析器
 运行并报告你的代码中的任何的错误和警告。你的IDE的这个Dart插件应当利用了Dart的解释引擎，但是你也自己在命令行中运行这个分析器
####代码规范器
 规范你的代码格式，按照<a href="https://www.dartlang.org/guides/language/effective-dart/style">dart风格规范</a>的要求，你的IDE通常就会允许你来规范化你的代码风格。
 
##11. 指引你到其他社区社区寻求dart相关问题帮助的解释部分

在**dart**语言的官网上的**Community** 

Community and Support，可以找到很多帮助。除此之外，**CDSN**,**ITeye**,**脚本之家**，**开源中国社区**也有很多关于**dart**的专业帮助。

##12. 从web storm软件菜单找出webstrom 中dart开发的帮助文档

打开**webstorm**，直接按f1，然后搜索**dart**，可以找到很多**dart**的开发知识。
###dart support
https://www.jetbrains.com/help/webstorm/2016.2/dart-support.html?search=dart
https://www.jetbrains.com/help/webstorm/2016.2/dart.html?search=dart
https://www.jetbrains.com/help/webstorm/2016.2/testing-dart.html?search=dart


----------
