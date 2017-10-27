# Building a Layer Hierarchy {#pageTitle}

## Arranging Layers into a Layer Hierarchy

#### Adding, Inserting, and Removing Sublayers

#### Positioning and Sizing Sublayers

最好生成layer时指定size，position是anchor相对于superLayer的位置

#### How Layer Hierarchies Affect Animations

`speed`、`rotate`、`opacity`

## Adjusting the Layout of Your Layer Hierarchies

只有自己创建layer对象的情况下，layer层的布局才会被用到

#### ~~Using Constraints to Manage Your Layer Hierarchies in OS X~~

#### ~~Setting Up Autoresizing Rules for Your OS X Layer Hierarchies~~

通过实现layer代理的`layoutSublayersOfLayer: `

通过继承子类并覆盖`layoutSublayers`

## Sublayers and Clipping

`masksToBounds`默认是NO

## Converting Coordinate Values Between Layers

* `convertPoint:fromLayer:`

* `convertPoint:toLayer:`

* `convertRect:fromLayer:`

* `convertRect:toLayer:`

* `convertTime:fromLayer:`

* `convertTime:toLayer:`





  


