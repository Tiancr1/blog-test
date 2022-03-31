# HTML入门笔记
## HTML起源
HTML作为定义万维网的基本规则之一，最初由蒂姆·本尼斯李（Tim Berners-Lee）于1989年在CERN（Conseil Europeen pour la Recherche Nucleaire）研制出来。
## HTML起手式
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
1. DOCTYPE含义是文档类型，目的是传达应该用什么语言进行解析。
2. html lang="en"指的是当前页面语言为英语，通常可以改成lang="zh-CN"
3. charset="UTF-8" 指的是当前的字符编码，不需要进行修改
## HTML标签
1. 标题h1~h6
2. 章节 section
3. 文章article
4. 段落 p
5. 头部 header
6. 脚部 footer
7. 主要内容 main
8. 旁支内容 aside
9. 划分 div
## HTML全局属性
1. class
2. contenteditable 可编辑的	
3. hidden
4. id
5. style
6. tabindex  键盘tab键访问功能，值为0代表最后一个访问，为1是第一个访问，-1是不访问
7. title

## HTML常用内容标签
1. ol+li   有序列表
2. ul+li   无序列表
3. dl+dt+dd   描述列表
4. pre  该标签包裹的部分可以保留任意空格和回车
5. hr  分割线
6. br  换行
7. a  超链接
8. em  强调，默认样式是斜体
9. strong 加粗
10. code 代码，默认样式等距
11. quote 引用
12. blockquote  块的引用