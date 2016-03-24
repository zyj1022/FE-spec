# CSS通用编码规范
==========

## 1 前言

本文档的目标是使 CSS 代码在团队中风格保持一致，容易被理解和被维护。
尽管本文档是针对 CSS 设计的，但是在使用各种 CSS 的预编译器(如 less、sass、stylus 等)时，适用的部分也应尽量遵循本文档的约定。

## 2 CSS命名方式
- 保持 class 命名为全小写，可以使用短划线（不要使用下划线和 camelCase 驼峰式命名）
- 短划线应该作为相关类的自然间断。(例如，.btn 和 .btn-blue)。
- 避免过度使用简写。.btn 可以很好地描述 button，但是 .t 不能代表任何元素。
- class 的命名应该尽量短，也要尽量明确。
- 使用有意义的名称；使用结构化或者作用目标相关，而不是抽象的名称。
- 全局通用命名时，需要加特定前缀如 `zk-wrap`
- 局部命名时，可以根据模块内容或就近父节点为前缀 

## 3 CSS基础设施

- 编码格式：文件编码格式 `UTF-8` 编码,在CSS文件顶格位置申明文档的编码charset

        @charset "utf-8";
    

## 4 编码风格
- 缩进方式：使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。
- 空格 
   - `选择器` 与 `{` 之间必须包含空格。
   -  `属性名` 与之后的 `:` 之间不允许包含空格， `:` 与 `属性值` 之间必须包含空格。
   - `列表型属性值` 书写在单行时，`,` 后必须跟一个空格。
- 选择器
    - 如无必要，不得为 `id`、`class` 选择器添加类型选择器进行限定。
    - 选择器的嵌套层级应不大于 `3` 级，位置靠后的限定条件应尽可能精确
    - `>`、`+`、`~` 选择器的两边各保留一个空格。
- 属性
    - 属性定义必须另起一行。
    - 属性定义后必须以分号结尾。
    - 在可以使用缩写的情况下，尽量使用属性缩写。
    - 属性前缀，标准属性放在最后，按冒号对齐方便阅读，也便于在编辑器内进行多行编辑。
    
            .box {
            -webkit-box-sizing: border-box;
               -moz-box-sizing: border-box;
                    box-sizing: border-box;
            }
    
- 属性书写顺序: 位置 > 盒模型 > 排版 > 外观 > 其它
    - Positioning 位置
            
            // 包括 float、display、overflow……
            position: absolute;
            top: 50px;
            left: 0;
            overflow-x: hidden;
            
    - Box model 盒模型
        
            border: 1px solid #000
            margin: 20px;
            padding: 15px;
            width: 240px;
            height: 160px;  
                          
    - Typographic 排版

            font-size: 16px;
            line-height: 32px;
            text-align: left;
            word-wrap: break-word
    
    - Visual 外观
    
            background: #fff url(images/logo.png) no-repeat;
            color: #000;


- 清除浮动
当子内容 float 浮动后，父级标签一定要清除浮动，通过对伪类设置 `clear` 的方式进行 `clearfix`。尽量不使用增加空标签的方式。[[参看]](http://cssmojo.com/latest_new_clearfix_so_far/)

        // css 
        .clearfix::after {
            clear: both;
            content: "";
            display: table; 
        }
    
- 颜色
    - RGB颜色值必须使用十六进制记号形式 `#rrggbb`。不允许使用 `rgb()`。
    - 颜色值可以缩写时，必须使用缩写形式, `border-color: #ccc;`
    - 颜色值不要使用英文命名色值,如 `color:red`
    - 颜色值最好全部采用小写字符
- 数值
    - 当数值为0时，可以省略单位， `padding: 0; margin: 0;`
    - 当数值为 0 - 1 之间的小数时，省略整数部分的 `0`,如 `opacity: .8;`
- z-index 一般以 5或10 为一个步长（如50,60,70），方便以后增加或修改
- !important' 尽量不使用 `!important` 声明。
- 字体
    - `font-family` 属性中的字体族名称应使用字体的英文 `Family Name`，其中如有空格，须放置在引号中。
    - 所谓英文 Family Name，为字体文件的一个元数据，常见名称如下：
    
        字体 | 操作系统 | Family Name
        -----|----------|------------
        宋体 (中易宋体) | Windows | SimSun
        黑体 (中易黑体) | Windows | SimHei
        微软雅黑 | Windows | Microsoft YaHei
        微软正黑 | Windows | Microsoft JhengHei
        华文黑体 | Mac/iOS | STHeiti
        冬青黑体 | Mac/iOS | Hiragino Sans GB
        文泉驿正黑 | Linux | WenQuanYi Zen Hei
        文泉驿微米黑 | Linux | WenQuanYi Micro Hei

            //css用法
            h1 {
                font-family: "Microsoft YaHei";
            }
- 字号
    - 需要在 Windows 平台显示的中文内容，其字号应不小于 `12px`。     
- 字重
    - CSS 的字重分 100 – 900 共九档，但目前受字体本身质量和浏览器的限制，实际上支持 `400` 和 `700` 两档，分别等价于关键词 `normal` 和 `bold`
- 行高
    - `line-height` 默认全局定义为 1.5 比较舒适，可根据实际情况调整    
- Hack 针对某个浏览器写的样式或某个浏览器BUG的样式，必须加上注释说明
        
        // css
        .clearfix{
            zoom:1; /* for IE6 IE7 */
        }