# HTML常用标签

## a标签的用法

1. 属性
   * href （拆解：hyper+reference ——超级引用，即链接）
   * target （跳转的目标）
2. href的取值
   * 网址
   * 路径
   * 伪协议
    ```html
        <a href="https://baidu.com" target="_blank">超链接</a>
        <a href="/a/b/c.html">c.html</a>
        <a href="index.html">index.html</a>
        <a href="./index.html">index.html</a>
        <a href="javascript:alert(1);">Javascript伪协议</a>
        <a href="javascript:;">空的伪协议</a>
        <a href="#xxx">查看xxx</a>
        <a href="mailto:1176417901@qq.com">发邮件给qq邮箱</a>
        <a href="tel:18613372819">打电话给自己</a>
    ```
3. target的取值
   * _blank  在空白页面打开
   * _top  在最顶层页面打开
   * _parent  在上一层级打开
   * _self  在当前页面打开（默认）
   ```html
   <a href="https://baidu.com" target="_blank">target页面</a>
   <a href="https://baidu.com" target="_top">target页面</a>
   <a href="https://baidu.com" target="_parent">target页面</a>
   <a href="https://baidu.com" target="_self">target页面</a>
   ```

## img标签的用法
1. 属性
   * src——图片地址
   * alt——图片加载失败时展示的文字
   * height——高度
   * width——宽度（只写宽或者高就可以，因为会自适应，如果都写容易使图片变形）
    ```html
    <img id=xxx width="400" src="dog.jpg" alt="狗子">
    ```
2. 事件
   * onload
   * onerror
    ```html
    <body>
        <img id=xxx src="dog.jpg" alt="狗子">
        <script>
            xxx.onload=function(){
                console.log('图片加载成功')
            };
            xxx.onerror=function(){
                console.log('图片加载失败')
            };
        </script>
    </body>
    ```
3. 响应式
   ```html
   <style>
        img{
            max-width: 100%;
        }
    </style>
   ```
## table标签的用法
1. 相关标签
   * table
   * thead
   * tbody
   * tfoot
   * tr
   * td
   * th
    ```html
    <body>
    <table>
    <thead>
        <tr>
            <th>英语</th>
            <th>翻译</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>hyper</td>
            <td>超级</td>
        </tr>
        <tr>
            <td>target</td>
            <td>目标</td>
        </tr>
        <tr>
            <td>reference</td>
            <td>引用</td>
        </tr>
    </tbody>
    <tfoot></tfoot>
    </table>
    </body>
    ```
2. 相关样式
   * table-layout:outo(根据字数自适应宽度)
   * table-layout:fixed(等宽)
   * border-spacing: 0px(表格间距)
   * border-collapse: collapse(表格是否合并展示)
   ```html
   <style>
    table{
        width: 200px;
        border-spacing: 0px;
        border-collapse: collapse;
    }
    th,td{
        border: 2px solid slategray;
    }
    </style>
    ```