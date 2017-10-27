# Improving Animation Performance {#pageTitle}

## ~~Choose the Best Redraw Policy for Your OS X Views~~

## ~~Update Layers in OS X to Optimize Your Rendering Path~~

## General Tips and Tricks

#### Use Opaque Layers Whenever Possible

如果直接将图片赋值给layer的contents，无论opaque值如何，alpha通道自动被保留

#### Use Simpler Paths for CAShapeLayer Objects

对于复杂的图形，可以分解成多个简单的图形然后组合起来，因为绘制发生在CPU，组合发生在GPU

#### Set the Layer Contents Explicitly for Identical Layers

赋值图片给layer的contents时，不会额外申请内存

#### Always Set a Layer’s Size to Integral Values

#### Use Asynchronous Layer Rendering As Needed

在layer的代理`drawLayer:inContext:`或者view的`drawRect:`中，如果发现绘制影响性能，可以设置layer的`drawsAsynchronously`

#### Specify a Shadow Path When Adding a Shadow to Your Layer

Core Animation计算图形阴影很耗时，如果阴影不常变动，可以设置layer的`shadowPath`

