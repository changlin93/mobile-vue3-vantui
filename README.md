## vue3+ts、移动端适配、vantUI、代码风格统一的详细配置

> 适配所需依赖
> postcss、
> autoprefixer、
> postcss-loader、
> postcss-pxtorem

```javascript
// .postcssrc
module.exports = ({file}) => {
     const rootValue = file.dirname.includes(path.join('node_modules', 'vant'))
        ? 37.5
        : 75;
    return {
        plugins: {
            'postcss-pxtorem': {
                rootValue,
                propList: ['*'],
            },
            autoprefixer: {
                overrideBrowserslist: [
                'Android 4.1',
                'iOS 7.1',
                'Chrome > 31',
                'ff > 31',
                'ie >= 8',
                ],
            },
        },
    };
};
```

## vw 适配

> 所需依赖
> postcss、
> autoprefixer、
> postcss-loader、
> postcss-px-to-viewport

```javascript
const path = require('path');

module.exports = ({ file }) => {
    const designWidth = file.dirname.includes(path.join('node_modules', 'vant'))
        ? 375
        : 750;
    return {
        plugins: {
            autoprefixer: {
                overrideBrowserslist: [
                    'Android 4.1',
                    'iOS 7.1',
                    'Chrome > 31',
                    'ff > 31',
                    'ie >= 8',
                ],
            },
            'postcss-px-to-viewport': {
                unitToConvert: 'px', // 要转化的单位
                viewportWidth: designWidth, // UI设计稿的宽度
                unitPrecision: 6, // 转换后的精度，即小数点位数
                propList: ['*'], // 指定转换的css属性的单位，*代表全部css属性的单位都进行转换
                viewportUnit: 'vw', // 指定需要转换成的视窗单位，默认vw
                fontViewportUnit: 'vw', // 指定字体需要转换成的视窗单位，默认vw
                selectorBlackList: ['wrap'], // 指定不转换为视窗单位的类名，
                minPixelValue: 1, // 默认值1，小于或等于1px则不进行转换
                mediaQuery: true, // 是否在媒体查询的css代码中也进行转换，默认false
                replace: true, // 是否转换后直接更换属性值
                exclude: [/node_modules/], // 设置忽略文件，用正则做目录名匹配
                landscape: false, // 是否处理横屏情况
            },
        },
    };
};

```

## eslint + prettierrc 代码风格配置

```javascript
// .prettierrc
{
    // 每行末尾自动添加分号
    "semi": true,
    // 单引号
    "singleQuote": true,

    // tab缩进大小,默认为2
    "tabWidth": 4，
    /* 箭头函数参数括号 默认avoid 可选 avoid| always
     * avoid 能省略括号的时候就省略 例如x => x
     * always 总是有括号 就算是只有一个参数也要括号
    **/
    "arrowParens": "always",

    // 末尾不需要逗号
    "trailingComma": "all"
}
```

## .editorconfig 配置

```javascript
// .editorconfig
[*.{js,jsx,ts,tsx,vue}]
indent_style = space
indent_size = 4
trim_trailing_whitespace = true
insert_final_newline = true
```

## 处理标签默认样式

```css
/* reset.css */
/* 初始化 */
a,
abbr,
acronym,
address,
applet,
area,
article,
aside,
audio,
b,
base,
basefont,
bdi,
bdo,
big,
blockquote,
body,
br,
button,
canvas,
caption,
center,
cite,
code,
col,
colgroup,
datalist,
dd,
del,
details,
dir,
div,
dfn,
dialog,
dl,
dt,
em,
embed,
fieldset,
figcaption,
figure,
font,
footer,
form,
frame,
frameset,
h1,
h2,
h3,
h4,
h5,
h6,
head,
header,
hr,
html,
i,
iframe,
img,
input,
ins,
isindex,
kbd,
keygen,
label,
legend,
li,
link,
map,
mark,
menu,
menuitem,
meta,
meter,
nav,
noscript,
object,
ol,
optgroup,
option,
output,
p,
param,
pre,
progress,
q,
rp,
rt,
ruby,
s,
samp,
script,
section,
select,
small,
source,
span,
strike,
strong,
style,
sub,
summary,
sup,
table,
tbody,
td,
textarea,
tfoot,
th,
thead,
time,
title,
tr,
track,
tt,
u,
ul,
var,
video,
wbr,
xmp {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font: 14px/1 'PingFang SC', 'Microsoft YaHei', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

img {
  display: block;
  border: none;
}

dl,
li,
menu,
ol,
ul {
  list-style: none;
}

button,
input,
select,
textarea {
  box-sizing: border-box;
  outline: none;
}

a,
a:link,
a:visited,
a:hover,
a:active {
  text-decoration: none;
}

/* 浮动方式 */
.fl {
  float: left;
}

.fr {
  float: right;
}

.clear {
  overflow: hidden;
  clear: both;
  height: 0;
  font-size: 0;
}

.clearfix::after {
  display: block;
  visibility: hidden;
  clear: both;
  height: 0;
  font-size: 0;
  content: '';
}
```
