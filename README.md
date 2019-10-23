# 轱辘-一个vue UI组件



## 介绍

这是我在学习vue过程中做的一个Ui 框架，希望对你有用2019-6-28。

## 开始使用
1.添加css样式

    使用本框架前，请在css中开启 border-box
    ```
    *,*::before,*::after{ box-sizing:border-box}
    ```
    IE8及以上浏览器都支持此样式
    
    你还需要设置默认颜色等变量（后续会改为scss变量）
    ```
    html {
        --button-height: 32px;
        --font-size: 14px;
        --button-bg: white;
        --button-active-bg: #eee;
        --border-radius: 4px;
        --color: #333;
        --border-color: #999;
        --border-color-hover: #666
    }
    ```
    
    IE15 及以上浏览器都支持此样式
2.安装 gulu
```
npm i --save zzyo-test-1-1
```
3.引入 gulu
```
import {Button, ButtonGroup, Icon} from 'zzyo-test-1-1'
import 'zzyo-test-1-1/dist/index.css'

export default {
  name: 'app',
  components: {
    'g-button': Button,
    'g-icon': Icon
  }
}
```
