#JavaScript编码规范
==============
# 前言

本文档的目标是使 JavaScript 代码风格保持一致，容易被理解和被维护。
虽然本文档是针对 JavaScript 设计的，但是在使用各种 JavaScript 的预编译语言时(如 TypeScript 等)时，适用的部分也应尽量遵循本文档的约定。

# 1 文件命名
- 多个单词组成时，采用中划线连接方式，比如说：账号模型文件 account-model.js
 
# 2 文件编码
- 编码格式：JavaScript 文件使用无 `BOM` 的 `UTF-8` 编码。; 
        
# 3 代码风格
## 3.1 缩进
- 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。
- `switch` 下的 `case` 和 `default` 必须增加一个缩进层级。

          javascript
          // good
          switch (variable) {
              case '1':
                  // do...
                  break;
              case '2':
                  // do...
                  break;
              default:
                  // do...
          }
          // bad
          switch (variable) {
          case '1':
              // do...
              break;
          case '2':
              // do...
              break;
          default:
              // do...
          }

## 3.2 空格

- 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。

        javascript
        var a = !arr.length;
        a++;
        a = b + c;


- 用作代码块起始的左花括号 `{` 前必须有一个空格。

          // good
          if (condition) {
          }
        
          while (condition) {
          }
        
          function funcName() {
          }
        
          // bad
          if (condition){
          }
        
          while (condition){
          }
        
          function funcName(){
          }

- `if / else / for / while / function / switch / do / try / catch / finally` 关键字后，必须有一个空格。

          javascript
          // good
          if (condition) {
          }
          while (condition) {
          }
          (function () {
          })();
          // bad
          if(condition) {
          }
          while(condition) {
          }
          (function() {
          })();

- 在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格。

        javascript
        // good
        var obj = {
            a: 1,
            b: 2,
            c: 3
        };
        // bad
        var obj = {
            a : 1,
            b:2,
            c :3
        };
        
- 函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格。

         javascript
          // good
          function funcName() {
          }
          var funcName = function funcName() {
          };
          funcName();
          // bad
          function funcName () {
          }
          var funcName = function funcName () {
          };
          funcName ();


- `,` 和 `;` 前不允许有空格。如果不位于行尾，`,` 和 `;` 后必须跟一个空格。

          javascript
          // good
          callFunc(a, b);
        
          // bad
          callFunc(a , b) ;

- 在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()` 和 `[]` 内紧贴括号部分不允许有空格。

- 单行声明的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格。

        javascript
          // good
          var arr1 = [];
          var arr2 = [1, 2, 3];
          var obj1 = {};
          var obj2 = {name: 'obj'};
          var obj3 = {
              name: 'obj',
              age: 20,
              sex: 1
          };
        
          // bad
          var arr1 = [ ];
          var arr2 = [ 1, 2, 3 ];
          var obj1 = { };
          var obj2 = { name: 'obj' };
          var obj3 = {name: 'obj', age: 20, sex: 1};
          
- 行尾不得有多余的空格。

## 3.3 换行

- 每个独立语句结束后必须换行。
- 每行不得超过 `120` 个字符。
- 运算符处换行时，运算符必须在新行的行首。

          javascript
          // good
          if (user.isAuthenticated()
              && user.isInRole('admin')
              && user.hasAuthority('add-admin')
              || user.hasAuthority('delete-admin')
          ) {
              // Code
          }
        
          var result = number1 + number2 + number3
              + number4 + number5;
        
        
          // bad
          if (user.isAuthenticated() &&
              user.isInRole('admin') &&
              user.hasAuthority('add-admin') ||
              user.hasAuthority('delete-admin')) {
              // Code
          }
        
          var result = number1 + number2 + number3 +
              number4 + number5;


- 在函数声明、函数表达式、函数调用、对象创建、数组创建、`for` 语句等场景中，不允许在 `,` 或 `;` 前换行。

        javascript
          // good
          var obj = {
              a: 1,
              b: 2,
              c: 3
          };
          foo(
              aVeryVeryLongArgument,
              anotherVeryLongArgument,
              callback
          );
          // bad
          var obj = {
              a: 1
              , b: 2
              , c: 3
          };
          foo(
              aVeryVeryLongArgument
              , anotherVeryLongArgument
              , callback
          );

- 不同行为或逻辑的语句集，使用空行隔开，更易阅读。

        javascript
          // 仅为按逻辑换行的示例，不代表setStyle的最优实现
          function setStyle(element, property, value) {
              if (element == null) {
                  return;
              }
        
              element.style[property] = value;
          }
          
- [建议] 在语句的行长度超过 `120` 时，根据逻辑条件合理缩进。
- [建议] 对于 `if...else...`、`try...catch...finally` 等语句，推荐使用在 `}` 号后添加一个换行 的风格，使代码层次结构更清晰，阅读性更好。

          javascript
          if (condition) {
              // some statements;
          }
          else {
              // some statements;
          }
        
          try {
              // some statements;
          }
          catch (ex) {
              // some statements;
          }

## 3.4 语句

- 不得省略语句结束的分号。
- 在 `if / else / for / do / while` 语句中，即使只有一行，也不得省略块 `{...}`。

        javascript
          // good
          if (condition) {
              callFunc();
          }
        
          // bad
          if (condition) callFunc();
          if (condition)
              callFunc();
              
- 函数定义结束不用添加分号

        javascript
        // good
        function funcName() {
        }
        
        // bad
        function funcName() {
        };
        
        // 如果是函数表达式，分号是不允许省略的。
        var funcName = function () {
        };

- `IIFE` 必须在函数表达式外添加 `(`，非 `IIFE` 不得在函数表达式外添加 `(`。
    - IIFE = Immediately-Invoked Function Expression.
    额外的 ( 能够让代码在阅读的一开始就能判断函数是否立即被调用，进而明白接下来代码的用途。而不是一直拖到底部才恍然大悟。
    
            javascript
            // good
            var task = (function () {
               // Code
               return result;
            })();            
            var func = function () {
            };  
                      
            // bad
            var task = function () {
                // Code
                return result;
            }();            
            var func = (function () {
            });
        

## 3.5 命名

- `变量` 使用 `Camel命名法`。
    - 每行定义一个变量，最好在行末标明注释
    - 优先使用单引号（'）而不是双引号（"）表示字符常量
    
            javascript
            var className = $('#nav');
        
- `常量` 使用 `全部字母大写，单词间下划线分隔` 的命名方式。

        javascript
        var HTML_ENTITY = {};
        
- `函数`名称使用 `Camel命名法`。
    - 函数的 `参数` 使用 `Camel命名法`。

- `类` 使用 `Pascal命名法`。

        javascript
        function TextNode(options) {
        }
    
- 类的 `方法` / `属性` 使用 `Camel命名法`。

        javascript
        function TextNode(value, engine) {
            this.value = value;
            this.engine = engine;
        }
        
        TextNode.prototype.clone = function () {
            return this;
        };
    

- `类名` 使用 `名词`。
- `函数名` 使用 `动宾短语`。
- `boolean` 类型的变量使用 `is` 或 `has` 开头。

        javascript
        var isReady = false;
        var hasMoreCommands = false;
        

## 3.6 注释

- 单行注释
    - 必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。

- 多行注释
    - [建议] 避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。

- 文档化注释
    - 为了便于代码阅读和自文档化，以下内容必须包含以 `/**...*/` 形式的块注释中。

## 3.7 类型定义

- 类型定义都是以 `{` 开始, 以 `}` 结束。
    常用类型如：{string}, {number}, {boolean}, {Object}, {Function}, {RegExp}, {Array}, {Date}。
    类型不仅局限于内置的类型，也可以是自定义的类型。比如定义了一个类 Developer，就可以使用它来定义一个参数和返回值的类型。

- 对于基本类型 {string}, {number}, {boolean}，首字母必须小写。

    | 类型定义         | 语法示例                                | 解释                                            |
    |------------------|-----------------------------------------|-------------------------------------------------|
    | String           | {string}                                | --                                              |
    | Number           | {number}                                | --                                              |
    | Boolean          | {boolean}                               | --                                              |
    | Object           | {Object}                                | --                                              |
    | Function         | {Function}                              | --                                              |
    | RegExp           | {RegExp}                                | --                                              |
    | Array            | {Array}                                 | --                                              |
    | Date             | {Date}                                  | --                                              |
    | 单一类型集合     | {Array.&lt;string&gt;\}                 | string 类型的数组                               |
    | 多类型           | {(number｜boolean)}                     | 可能是 number 类型, 也可能是 boolean 类型       |
    | 允许为null       | {?number}                               | 可能是 number, 也可能是 null                    |
    | 不允许为null     | {!Object}                               | Object 类型, 但不是 null                        |
    | Function类型     | {function(number, boolean)}             | 函数, 形参类型                                  |
    | Function带返回值 | {function(number, boolean):string}      | 函数, 形参, 返回值类型                          |
    | Promise          | Promise.&lt;resolveType, rejectType&gt; | Promise，成功返回的数据类型，失败返回的错误类型 |
    | 参数可选         | @param {string=} name                   | 可选参数, =为类型后缀                           |
    | 可变参数         | @param {...number} args                 | 变长参数, ...为类型前缀                         |
    | 任意类型         | \{*}                                    | 任意类型                                        |
    | 可选任意类型     | @param {*=} name                        | 可选参数，类型不限                              |
    | 可变任意类型     | @param {...*} args                      | 变长参数，类型不限                              |
    
- 文件注释
    - 文件顶部必须包含文件注释，用 `@file` 标识文件说明。
    - 文件注释中可以用 `@author` 标识开发者信息。

            javascript
            /**
             * @file Describe the file
             * @author author-name(mail-name@domain.com)
             *         author-name2(mail-name2@domain.com)
             */



- 函数/方法注释
    - 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识。
    - 参数和返回值注释必须包含类型信息，且不允许省略参数的说明。
    - 当函数是内部函数，外部不可访问时，可以使用 `@inner` 标识。

            javascript
            /**
             * 函数描述
             *
             * @param {string} p1 参数1的说明
             * @param {string} p2 参数2的说明，比较长那就换行了.
             * @param {number=} p3 参数3的说明（可选）
             * @return {Object} 返回值描述
             */
            function foo(p1, p2, p3) {
                var p3 = p3 || 10;
                return {
                    p1: p1,
                    p2: p2,
                    p3: p3
                };
            }
            
- 对 Object 中各项的描述， 必须使用 `@param` 标识。

        javascript
        /**
         * 函数描述
         *
         * @param {Object} option 参数描述
         * @param {string} option.url option项描述
         * @param {string=} option.method option项描述，可选参数
         */
        function foo(option) {
            // TODO
        }

- [建议] 重写父类方法时， 应当添加 `@override` 标识。如果重写的形参个数、类型、顺序和返回值类型均未发生变化，可省略 `@param`、`@return`，仅用 `@override` 标识，否则仍应作完整注释。


# 4 语言特性
----------

## 4.1 变量

- 变量、函数在使用前必须先定义。
- 每个 `var` 只能声明一个变量。

- 变量必须 `即用即声明`，不得在函数或其它形式的代码块起始位置统一声明所有变量。
    变量声明与使用的距离越远，出现的跨度越大，代码的阅读与维护成本越高。虽然JavaScript的变量是函数作用域，还是应该根据编程中的意图，缩小变量出现的距离空间。

        javascript
        // good
        function kv2List(source) {
            var list = [];
            for (var key in source) {
                if (source.hasOwnProperty(key)) {
                    var item = {
                        k: key,
                        v: source[key]
                    };
                    list.push(item);
                }
            }
            return list;
        }
        
        // bad
        function kv2List(source) {
            var list = [];
            var key;
            var item;
        
            for (key in source) {
                if (source.hasOwnProperty(key)) {
                    item = {
                        k: key,
                        v: source[key]
                    };
                    list.push(item);
                }
            }        
            return list;
        }
        
## 4.2 条件

- 在 Equality Expression 中使用类型严格的 `===`。仅当判断 `null` 或 `undefined` 时，允许使用 `== null`。
- 对于相同变量或表达式的多值条件，用 `switch` 代替 `if`。


## 4.3 循环

- [建议] 不要在循环体中包含函数表达式，事先将函数提取到循环体外。
    - 循环体中的函数表达式，运行过程中会生成循环次数个函数对象。

            javascript
            // good
            function clicker() {
                // ......
            }
            
            for (var i = 0, len = elements.length; i < len; i++) {
                var element = elements[i];
                addListener(element, 'click', clicker);
            }
            
            
            // bad
            for (var i = 0, len = elements.length; i < len; i++) {
                var element = elements[i];
                addListener(element, 'click', function () {});
            }

- 对循环内多次使用的不变值，在循环外用变量缓存。

        javascript
        // good
        var width = wrap.offsetWidth + 'px';
        for (var i = 0, len = elements.length; i < len; i++) {
            var element = elements[i];
            element.style.width = width;
            // ......
        }
        
        // bad
        for (var i = 0, len = elements.length; i < len; i++) {
            var element = elements[i];
            element.style.width = wrap.offsetWidth + 'px';
            // ......
        }

## 4.4 类型

### 4.4.1 类型检测
- 类型检测优先使用 `typeof`。对象类型检测使用 `instanceof`。`null` 或 `undefined` 的检测使用 `== null`。

        javascript
        // string
        typeof variable === 'string'
        
        // number
        typeof variable === 'number'
        
        // boolean
        typeof variable === 'boolean'
        
        // Function
        typeof variable === 'function'
        
        // Object
        typeof variable === 'object'
        
        // RegExp
        variable instanceof RegExp
        
        // Array
        variable instanceof Array
        
        // null
        variable === null
        
        // null or undefined
        variable == null
        
        // undefined
        typeof variable === 'undefined'
    
### 4.4.1 类型转换

- [建议] 转换成 `string` 时，使用 `+ ''`。

        javascript
        // good
        num + '';
        
        // bad
        new String(num);
        num.toString();
        String(num);

- [建议] 转换成 `number` 时，通常使用 `+`。

        javascript
        // good
        +str;
        
        // bad
        Number(str);

- [建议] `string` 转换成 `number`，要转换的字符串结尾包含非数字并期望忽略时，使用 `parseInt`。

        javascript
        var width = '200px';
        parseInt(width, 10);

- [强制] 使用 `parseInt` 时，必须指定进制。

        javascript
        // good
        parseInt(str, 10);
        
        // bad
        parseInt(str);

- [建议] 转换成 `boolean` 时，使用 `!!`。

        javascript
        var num = 3.14;
        !!num;

- [建议] `number` 去除小数点，使用 `Math.floor` / `Math.round` / `Math.ceil`，不使用 `parseInt`。

        javascript
        // good
        var num = 3.14;
        Math.ceil(num);
        
        // bad
        var num = 3.14;
        parseInt(num, 10);

## 4.5 字符串

- [强制] 字符串开头和结束使用单引号 `'`。
    1.	输入单引号不需要按住 `shift`，方便输入。
    2.	实际使用中，字符串经常用来拼接 HTML。为方便 HTML 中包含双引号而不需要转义写法。
    
            javascript
            var str = '我是一个字符串';
            var html = '<div class="cls">拼接HTML可以省去双引号转义</div>';
    
- 使用 `数组` 或 `+` 拼接字符串。
    1.	使用 `+` 拼接字符串，如果拼接的全部是 StringLiteral，压缩工具可以对其进行自动合并的优化。所以，静态字符串建议使用 `+` 拼接。
    2.	在现代浏览器下，使用 `+` 拼接字符串，性能较数组的方式要高。
    3.	如需要兼顾老旧浏览器，应尽量使用数组拼接字符串。

            javascript
            // 使用数组拼接字符串
            var str = [
                // 推荐换行开始并缩进开始第一个字符串, 对齐代码, 方便阅读.
                '<ul>',
                    '<li>第一项</li>',
                    '<li>第二项</li>',
                '</ul>'
            ].join('');
            
            // 使用 `+` 拼接字符串
            var str2 = '' // 建议第一个为空字符串, 第二个换行开始并缩进开始, 对齐代码, 方便阅读
                + '<ul>',
                +    '<li>第一项</li>',
                +    '<li>第二项</li>',
                + '</ul>';
            

- [建议] 使用字符串拼接的方式生成HTML，需要根据语境进行合理的转义。

        javascript
        // HTML 转义
        var str = '<p>' + htmlEncode(content) + '</p>';
        
        // HTML 转义
        var str = '<input type="text" value="' + htmlEncode(value) + '">';
        
        // URL 转义
        var str = '<a href="/?key=' + htmlEncode(urlEncode(value)) + '">link</a>';
        
        // JavaScript字符串 转义 + HTML 转义
        var str = '<button onclick="check(\'' + htmlEncode(strLiteral(name)) + '\')">提交</button>';


- [建议] 复杂的数据到视图字符串的转换过程，选用一种模板引擎。
    - 使用模板引擎有如下好处：
    - 在开发过程中专注于数据，将视图生成的过程由另外一个层级维护，使程序逻辑结构更清晰。
    - 优秀的模板引擎，通过模板编译技术和高质量的编译产物，能获得比手工拼接字符串更高的性能。
    - 模板引擎能方便的对动态数据进行相应的转义，部分模板引擎默认进行HTML转义，安全性更好。    
    - artTemplate: 体积较小，在所有环境下性能高，语法灵活。
    - dot.js: 体积小，在现代浏览器下性能高，语法灵活。
    - etpl: 体积较小，在所有环境下性能高，模板复用性高，语法灵活。
    - handlebars: 体积大，在所有环境下性能高，扩展性高。
    - hogon: 体积小，在现代浏览器下性能高。
    - nunjucks: 体积较大，性能一般，模板复用性高。