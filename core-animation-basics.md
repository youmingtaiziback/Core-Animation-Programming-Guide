# Core Animation Basics {#pageTitle}

Core Animation在图形硬件上管理可视内容。通过改变属性来实现动画

## Layers Provide the Basis for Drawing and Animations

layer是3D空间的2D表示，动画的核心内容，存储位图的状态信息，是view的model

#### The Layer-Based Drawing Model

属性改变触发动画时，Core Animation将位图和状态信息传递给图形硬件做渲染

基于view的图形会利用CPU在主线程调用`drawRect:`，很耗时

#### Layer-Based Animations

把layer的数据和状态信息与视觉表现分离，有利于把Core Animation插入到中间并做动画

## Layer Objects Define Their Own Geometry

#### Layers Use Two Types of Coordinate Systems

point-based coordinate systems 和 unit coordinate systems

iOS app中不建议使用`geometryFlipped`

#### Anchor Points Affect Geometric Manipulations

改变anchor对position和transform的影响

#### Layers Can Be Manipulated in Three Dimensions

`transform`改变layer和他的sublayers， `sublayerTransform`多用于透视

Core Animation提供了一些生成变化矩阵的方法，还支持通过KVC改变矩阵

## Layer Trees Reflect Different Aspects of the Animation State

Core Animation管理着三种layer对象

* model layer tree（layer tree）保存动画的目标值
* presentation tree：表示动画过程中的值
* render tree：Core Animation私有

![](/assets/impor1t.png)

## The Relationship Between Layers and Views

layer不能接收事件、绘制内容、参与响应链

iOS中layer和view一对一

iOS里面的view默认是layer-backed view，对于这样的view，建议直接操作view而不是layer

