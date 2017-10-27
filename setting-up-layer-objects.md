# Setting Up Layer Objects {#pageTitle}

## Enabling Core Animation Support in Your App

iOS app中，core animation自动被启用，每一个view都是layer-back view

## Changing the Layer Object Associated with a View

不同类型的layer提供不同的功能

#### Changing the Layer Class Used by UIView

```
+ (Class) layerClass {
    return [CAMetalLayer class];
}
```

#### ~~Changing the Layer Class Used By NSView~~

#### ~~Layer Hosting Lets You Change the Layer Object in OS X~~

#### Different Layer Classes Provide Specialized Behaviors

| Class | Usage |
| :--- | :--- |
| CAEmitterLayer | 生成粒子发射器 |
| CAGradientLayer | 渐变 |
| CAMetalLayer | 用于Metal |
| CAEAGLLayer | OpenGL ES |
| CAReplicatorLayer | 自动复制sublayers |
| CAScrollLayer | 管理由多个sublayers组成的大的可滚动的区域 |
| CAShapeLayer | 根据贝塞尔路径画图形，在主线程渲染形状缓存结果 |
| CATextLayer | 渲染普通或者attributed string |
| CATiledLayer | 把一个大图片分割成小的独立渲染，并支持缩放 |
| CATransformLayer | 渲染3Dlayer层次 |

## Providing a Layer’s Contents

为layer管理的位图提供内容有三种方式：

* 把图片赋给layer.contents
* 通过代理绘制
* 通过子类覆盖绘制函数

只有在创建自己的layer对象的时候，才需要调用以上三种情况。layer-backed view会选择最高效的方式为layer赋值

#### Using an Image for the Layer’s Content

通过layer.contents赋值不会copy图片，节省内存

赋值时要保证图片和设备的分辨率相同

#### Using a Delegate to Provide the Layer’s Content

代理可以实现的方法有：

* `displayLayer:` 创建位图并赋给layer.contents
* `drawLayer:inContext:` Core Animation创建好了位图和绘图环境，开发者只需要绘制

layer-backed view自动设置为layer的代理并实现了相关代理方法，开发者只需要实现`drawRect:`

#### Providing Layer Content Through Subclassing

集成可以实现的子类方法有：

* 在display里面给contents属性赋值
* 覆盖drawInContext:并在给定的环境下绘制 

display是更新layer内容的总入口

#### Tweaking the Content You Provide

图片赋值给`contents`时，layer的`contentsGravity`属性决定了图片位置

`contentsGravity`有两类：

* 位置
* 伸缩

#### Working with High-Resolution Images

给layer.contents设置图片时，需要指定其contentsScale，默认值是1.0

给layer-backed view设置图片时，UIKit会自动设置contentsScale值

## Adjusting a Layer’s Visual Style and Appearance

#### Layers Have Their Own Background and Border

考虑到sublayers的情况，backgroundColor在contents的下面，border在所有sublayers的上面

用pattern image给backgroundColor赋值时，Core Graphics会渲染pattern image，但是Core Graphics和layer的坐标不同，会出现上下颠倒的情况

如果背景颜色是纯色，可以设置layer.opaque为YES，这样可以提升性能。如果用圆角就不能把layer.opaque设为YES

#### Layers Support a Corner Radius

圆角使用了透明蒙版，当masksToBounds设置为NO时，不影响contents和sublayers的显示；如果设置为YES，会切掉圆角以外的部分

#### Layers Support Built-In Shadows

layer shadow的opacity默认值是0，shadow默认在layer正下方

shadow也是layer的content的一部分，收到masksToBounds的影响

#### ~~Filters Add Visual Effects to OS X Views~~

## ~~The Layer Redraw Policy for OS X Views Affects Performance~~

## Adding Custom Properties to a Layer

CAAnimation和CALayer类支持通过KVC添加自定义属性，可以把action关联到自定义属性来执行相应动画

## Printing the Contents of a Layer-Backed View



