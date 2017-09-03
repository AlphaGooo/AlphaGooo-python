python的脚本程序放在 spider 里面

## 1. 测试要获取下载图片的整个页面信息：

```
import urllib

def getHtml(url):
    page = urllib.urlopen(url)
    html = page.read()
    return html

html = getHtml("http://tieba.baidu.com/p/2738151262")

print html
```

## 2. 测试获取想要的页面图片信息：

```
import re
import urllib

def getHtml(url):
    page = urllib.urlopen(url)
    html = page.read()
    return html


def getImg(html):
    reg = r'src="(.+?\.jpg)" pic_ext'
    imgre = re.compile(reg)
    imglist = re.findall(imgre, html)
    return imglist

html = getHtml("http://tieba.baidu.com/p/2460150866")
print getImg(html)
```

## 3. 测试获取网页的所有图片并下载到本地：

```
import urllib
import  re

def getHtml(url):
    page = urllib.urlopen(url)
    html = page.read()
    return html

def getImg(html):
    reg = r'src="(.+?\.jpg)" pic_ext'
    imgre = re.compile(reg)
    imglist = re.findall(imgre,html)
    x = 0
    for imgurl in imglist:
        print x
        urllib.urlretrieve(imgurl,'%s.jpg' % x)
        x+=1

html = getHtml("http://tieba.baidu.com/p/2460150866")
print getImg(html)
```
