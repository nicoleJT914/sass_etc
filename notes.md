## sass的应用场景：
主要是sass-loader与webpack的结合使用
## 运行  
运行时可以使用`sass input.scss output.css`  
也可以用shell脚本运行`sh ./build.sh`  
## 语法
[sass document](http://sass.bootcss.com/docs/sass-reference/)  
sass比较核心的部分：
### 嵌套规则
不仅选择器可以进行嵌套，属性也是可以进行嵌套的
### 父选择符：`&`
### 变量
使用形如`$width`来代表变量，在属性值中可以使用变量。需要注意的是变量也是有作用域的，获取变量值时也会先在最近的嵌套中寻找，找不到会向上寻找。  
另外还有插值，我觉得跟变量差不多，只不过用在选择器和属性名中（虽然插值也可以用在属性值中，但是会被编译器视为纯CSS，这点是要注意的）。插值的形式为`${}`，需要的是我们在写CSS，所以任何选择器不要加“”，会报错的。
### 运算
在sass中可以进行运算，为开发提供了很大的便利。  
注意在运算中不要写`font: 10px/2px`，这会被编译为纯CSS，可以用圆括号包起来。  
### 指令@
指令这是一大块，常用的就是`@import`,`@extend`,`@mixin`这三个。

- `@import`  
跟CSS中一样，我们也可以使用`@import`引入其他的scss文件，如果不加后缀，编译时会自动添加。  

- `@extend`  
有一点像java中的extend，也就是继承的意思。  
给.box2应用`@extend .box1`会把.box1中所有的规则复制到.box2下，包括其中的所有嵌套！  
给一个选择器应用多个继承指令时，实际的编译规则可能跟我们想的并不一致，建议去看一下输出的CSS文件，sass是把该选择器加到要继承的规则中，而不是把要继承的规则复制一份下来。

- `@mixin`
`@mixin`和`@include`需要配套使用，`@mixin`定义一个CSS属性集合，而`@include`负责引用，有点像animation和@keyframes的用法。  
`@mixin`的使用方法相当灵活，还可以写成函数形式进行传参`@mixin dashed-border($color, $width)`,`@include dashed-border(blue, 2px)`

花了2个小时看了一下sass，看的很粗略，以上大概就是我觉得比较重要的内容，肯定有不对的地方，以后用到的时候再滚回来改吧！

