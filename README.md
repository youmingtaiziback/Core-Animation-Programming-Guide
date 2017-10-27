# About Core Animation1 {#pageTitle}

Core Animation绘制每一帧，你只需要配置参数并启动动画。Core Animation在图形硬件上加速渲染，减轻CPU负担

![](/assets/import.png)

## At a Glance

#### Core Animation Manages Your App’s Content

Core Animation不是绘制系统，在硬件上组合操作app内容。layer把app可是部分放进位图以便于硬件操作。

#### Layer Modifications Trigger Animations

改变一个layer的属性值会触发隐士动画，如果想更精细的控制，可选择显示动画

#### Layers Can Be Organized into Hierarchies

layer的层次关系和view的层次关系类似

#### Actions Let You Change a Layer’s Default Behavior

隐士动画通过预定义的action object完成。可以自定义action object，并赋给layer的属性。属性变化时会触发action object

## How to Use This Document

本文档帮助开发者对动画进行更多的控制，或者提升绘制性能

## Prerequisites

[_View Programming Guide for iOS_](https://developer.apple.com/library/content/documentation/WindowsViews/Conceptual/ViewPG_iPhoneOS/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009503)

## See Also

## 



