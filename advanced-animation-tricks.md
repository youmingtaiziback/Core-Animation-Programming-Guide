# Advanced Animation Tricks {#pageTitle}

基于属性的动画、关键帧动画。多个动画同时发生、顺次发生

## Transition Animations Support Changes to Layer Visibility

transition动画通过操作layer缓存的图片创建视觉效果

创建`CATransition`对象并赋值给参与动画的图层

## Customizing the Timing of an Animation

`CAMediaTiming`定义了为Core Animation提供时间信息的方法，Core Animation中`CAAnimation`和`CALayer`实现了该协议

每一个layer有自己的本地时间，默认情况下，不同的layer之间的时间认为是同步的。但是本地时间可能被改变，所以需要时间转换

事件相关属性：

* beginTime：延迟动画开时的情况中，需要将`fillMode`设置为`kCAFillModeBackwards`，这样动画就可以从开始值启动。否则动画会先跳到最终值然后启动
* `autoreverses、repeatCount`
* group animations的`timeOffset`

## Pausing and Resuming Animations

暂停和重启动画可以用`CAMediaTiming`协议的`speed`属性

## Explicit Transactions Let You Change Animation Parameters

CATransaction管理者动画的创建和分组并在合适的时候执行。大多数情况下系统自动创建，也可以自己创建

创建显示transaction

```
[CATransaction begin];
theLayer.zPosition=200.0;
theLayer.opacity=0.0;
[CATransaction commit];
```

显示transaction可以修改各个参数并设置完成的回调，修改参数以`setValue:forKey:`方式完成

如果想为不同的动画提供不同的参数，可以嵌套transaction

## Adding Perspective to Your Animations

```
CATransform3D perspective = CATransform3DIdentity;
perspective.m34 = -1.0/eyePosition;

// Apply the transform to a parent layer.
myParentLayer.sublayerTransform = perspective;
```



