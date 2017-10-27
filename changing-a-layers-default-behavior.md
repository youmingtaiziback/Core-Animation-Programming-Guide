# Changing a Layer’s Default Behavior {#pageTitle}

隐士动画通过action对象完成，action对象遵守CAAction协议，所有CAAnimation对象都实现了CAAction协议，属性被改变时，这些action对象被执行

## Custom Action Objects Adopt the CAAction Protocol

创建action对象需要实现`CAAction`协议的`runActionForKey:object:arguments:`方法

定义action对象时，必须制定action对象如何被触发。在以下情况下会被触发：

* layer的一个属性被改变，可以是任意属性，包括自定义属性
* `kCAOnOrderIn`：layer变得可视或者添加到layer层次中
* `kCAOnOrderOut`：layer从层次中删除
* `kCATransition`：layer马上开始transition动画

## Action Objects Must Be Installed On a Layer to Have an Effect

当事件发生时，layer通过调用`actionForKey:`搜索action对象来执行

Core Animation寻找action对象的顺序如下：

* layer代理实现的`actionForLayer:forKey:`方法
  * 返回action对象
  * 返回nil搜索继续
  * 返回NSNull搜索继续 
* layer在它的`actions`中查找key
* 在layer的style字典中查找包含key的字典
* `[layer defaultActionForKey:];`
* layer执行由Core Animation定义的隐士action

找到action之后，layer调用action的`runActionForKey:object:arguments:`方法执行action

在哪里提供action视情况而定：

* 特定情况下或者layer已经有delegate了，使用代理并实现`actionForLayer:forKey:`
* 不用代理的layer，把action添加到actions中
* 与自定义属性有关的action，把action放到style字典里
* 对layer来说是一个基本行为的话，在layer的子类覆盖`defaultActionForKey:`

## Disable Actions Temporarily Using the CATransaction Class

```
[CATransaction begin];
[CATransaction setValue:(id)kCFBooleanTrue forKey:kCATransactionDisableActions];
[aLayer removeFromSuperlayer];
[CATransaction commit];
```



