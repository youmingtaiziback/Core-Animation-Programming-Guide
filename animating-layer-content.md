# Animating Layer Content {#pageTitle}

## Animating Simple Changes to a Layer’s Properties

隐士动画中系统创建动画并设置属性的最终值，显示动画需要手动设置属性的最终值

隐士动画和显示动画都会在下一个runloop执行，多个动画会同时执行

## Using a Keyframe Animation to Change Layer Properties

关键帧动画让你提供一组时间和属性值，对于position，属性值可以是一条path

#### Specifying Keyframe Values

对于以点为单位的属性，关键帧动画的值可以用path提供

#### Specifying the Timing of a Keyframe Animation

* `calculationMode`
  * Linear and cubic animations：用给定的时间信息生成动画，灵活性最大 
  * Paced animations：不用`keyTimes`或者`timingFunctions`提供的时间信息，时间隐式生成
  * Discrete animations：从一个帧调到另一个帧，用keyTimes属性提供的值，忽略`timingFunctions`属性提供的值
* `keyTimes`不适用于Paced animations
* `timingFunctions` 

## Stopping an Explicit Animation While It Is Running

中途取消动画：

* `[layer removeAnimationForKey:];`
* `[layer removeAllAnimations];`

从layer里面不能直接取消隐士动画

动画取消后，系统用当前值绘制layer

## Animating Multiple Changes Together

`CAAnimationGroup`可以让多个动画同时进行，它的时间和时长会覆盖组里的个别动画的值

高级的动画成组执行可以使用transaction object

## Detecting the End of an Animation

* `[CATransaction setCompletionBlock:];`
* 设置`CAAnimation`的delegate并实现`animationDidStart:`、`animationDidStop:finished:`

两个动画要实现顺序执行的话用`beginTime`不用上述方法

## How to Animate Layer-Backed Views

对于layer-backed view，推荐使用UIKit的接口实现动画

#### Rules for Modifying Layers in iOS

UIView默认禁止了layer的动画，只有在animation block里面开启。所以在animation block外面的改变属性不会产生动画

#### ~~Rules for Modifying Layers in OS X~~

#### Remember to Update View Constraints as Part of Your Animation

动画前取消约束，动画后恢复约束  
  




