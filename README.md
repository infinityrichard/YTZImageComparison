

YTZImageComparison
==============

[![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://raw.githubusercontent.com/Job-Yang/YTZImageComparison/master/LICENSE)&nbsp;
[![CocoaPods](http://img.shields.io/cocoapods/v/YTZImageComparison.svg?style=flat)](http://cocoapods.org/?q=YTZImageComparison)&nbsp;
[![CocoaPods](http://img.shields.io/cocoapods/p/YTZImageComparison.svg?style=flat)](http://cocoapods.org/?q=YTZImageComparison)&nbsp;
[![Support](https://img.shields.io/badge/support-iOS%208%2B%20-blue.svg?style=flat)](https://www.apple.com/nl/ios/)&nbsp;

##总述

 YTZImageComparison是一个使用Objective-C编写，基于对图片颜色分析的一款取色，图片对比的开源库。实现了对图片优势色（主色）的提取，取出图片对应点颜色、对图片进行简单的相同/相似比较。其中取主色的算法借鉴了GitHub上的开源项目[ColorCube](https://github.com/pixelogik/ColorCube)。

##算法简介

#### 1. 提取图片主色的算法实现
- 将传入的图片重绘为小尺寸的图片，避免遍历所有像素点所带来的性能问题;
- 先得到重绘后图片的ARGB分量值；
- 将RGB这三个分量对应到以R,G,B作为空间直角坐标轴的分量(即得到颜色空间);
- 搜寻每个RGB对应点相邻方向的26个点(空间模型类似于三阶魔方)的RGB值，该点是否比旁边的点更加的"鲜艳";
- 如果是，则将他加入鲜艳色数组;
- 计算鲜艳色出现的频率，按照频率高低加入到返回值数组。
- 其中可根据多个枚举值来定制"鲜艳"的标准，也可以设置忽略一个RGB色彩空间的颜色，避免一些颜色的干扰。
 
 
#### 2. 提取图片对应点(像素)颜色的算法实现
- 将传入的图片重绘为小尺寸的图片;
- 先得到重绘后图片的ARGB分量值；
- 由参数Rect算出该像素ARGB信息在字符数组中的位置；
- 返回一个该ARGB分量组合成的UIColor。
 
 
#### 3. 图片相同的算法实现
- 将传入两张的图片重绘为相同的小尺寸的图片;
- 先得到重绘后图片的ARGB分量值；
- 计算对应像素在颜色空间上的距离，小于相等色差阀值则匹配度加一;
- 匹配度高于最低相等阀值则视为图片相同。
- 对于相同图片的算法主要是基于对像素的色差对比，这样的对比的结果是稳定的。

  
##效果图

**1. 提取图片主色**

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/MainColourDemo1.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/MainColourDemo2.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/MainColourDemo3.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/MainColourDemo4.png)


**2. 提取图片对应点(像素)颜色**

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/GetColourDemo1.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/GetColourDemo2.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/GetColourDemo3.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/GetColourDemo4.png)


**3. 图片相同**

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/EqualImageDemo1.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/EqualImageDemo2.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/EqualImageDemo3.png)

![YTZImageComparison](https://github.com/Job-Yang/YTZImageComparison/blob/master/ScreenShots/EqualImageDemo4.png)


##安装
### CocoaPods

1. 将 cocoapods 更新至最新版本.
2. 在 Podfile 中添加 `pod 'YTZImageComparison'`。
3. 执行 `pod install` 或 `pod update`。
4. 导入 `"YTZImageComparison.h"`。

### 手动安装

1. 下载 YTZImageComparison 文件夹内的所有内容。
2. 将 YTZImageComparison 内的源文件添加(拖放)到你的工程。
3. 导入 `YTZImageComparison.h`.


##许可证
YTZImageComparison 使用 MIT 许可证，详情见 LICENSE 文件。


