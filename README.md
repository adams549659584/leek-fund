# leek-fund

VSCode 插件，在编码的时候随时关注实时股票&基金数据。**因接口原因基金数据延迟 2 分钟左右，股票数据是实时**

**投资其实就是一次心态修炼，稳住心态长期投资都会有收益的！！**

## Screenshot

鼠标悬浮查看股票和基金实时数据截图：

![界面截图 1](https://ww1.sinaimg.cn/large/940e68eegy1ghcoqirahuj214w1pke73.jpg)

- [查看界面图片 2](http://ww1.sinaimg.cn/large/940e68eegy1ghcvziv655j20wm1aywnx.jpg)

## 插件配置说明

修改用户配置，添加你所需要监控的股票代码

```
  // 配置需要监控的股票代码
  // 可根据沪市深市分别加上sh、sz前缀，亦可不加
  // 不加前缀的情况下，6开头的代码默认加上sh，其余加上sz
  // 需要查看上证指数，代码为sh000001

  // 港股股票代码前面需要加上hk前缀，如hk09988即可监控阿里巴巴港股

  "leek-fund.stocks": [
    "0000001",
    "0000300",
    "0000016",
    "0000688",
    "0399006",
    "0000913",
    "0000905",
    "0600519",
    "0399975",
    "0399995",
    "hk09988"
  ],

  // 配置需要监控的基金代码
  "leek-fund.funds": [
    "001632",
    "420009",
    "320007",
    "003096",
    "001102",
    "003885",
    "001071",
    "005963",
    "005223",
    "002316",
    "161726",
    "161028",
    "519674",
    "161725"
  ],

  // 配置轮询请求最新数据的时间间隔
  "leek-fund.updateInterval": 10000


  // 配置股票涨的颜色，默认为white。为什么不是red，红色像是报错，很刺眼。
  "leek-fund.riseColor": "white"


  // 配置股票跌的颜色，默认为green
  "leek-fund.fallColor": "black"

  // 配置展示的时间段，默认为[9, 15]，每十分钟判断一下
  "leek-fund.showTime": [9, 15]


```

## 接口说明

> 需要学习开发的可以了解

爬取基金基本概况信息

```
http://fund.eastmoney.com/f10/jbgk_001632.html
```

只需要获取基金名称可以走 js，jsonp

```
http://fundgz.1234567.com.cn/js/001632.js?rt=1596338178723
```

爬取净值接口

```
// 历史净值
http://fund.eastmoney.com/f10/F10DataApi.aspx?type=lsjz&code=001632&page=1&&sdate=2020-07-31

或网易的api （股票实时数据，但基金无实时数据）
比如上证指数：
https://api.money.126.net/data/feed/0000001?callback=a

// 基金实时数据（有几分钟延迟，插件基金数据使用的是此接口）
// 比如诺安成长混合
http://fundgz.1234567.com.cn/js/320007.js?callback=a

```

// 图片

```
// 走势图片、[沪深拼音]/time/[图片大小]/[股票代码]
http://img1.money.126.net/chart/hs/time/210x140/1399001.png
```

基金代码列表

```
http://fund.eastmoney.com/js/fundcode_search.js
```

参考文章：

```
// 官方插件文档介绍
https://code.visualstudio.com/api/extension-guides/overview

// Python 爬取历史基金数据
https://blog.csdn.net/yuzhucu/article/details/55261024

// 发布流程
https://blog.csdn.net/Suwanqing_su/article/details/105947156

// 开发系列博文
http://blog.haoji.me/vscode-plugin-overview.html

```

## Github

https://github.com/giscafer/leek-fund
