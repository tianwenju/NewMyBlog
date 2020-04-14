---
title: Material-Ui 响应式布局
tags: [Material-Ui]
categories: [UI]
date: 2020-04-14 15:05:55
---
![photos](ui.jpg)
## [简介](https://material-ui.com/)
它是React组件，实现了谷歌Material Design设计规范。世界上最流行的React界面框架。
## [支持平台](https://material-ui.com/zh/getting-started/supported-platforms/)
Material-UI支持所有主流的稳定的浏览器，支持IE11以上。Material-UI还支持node.js v6.x以上的服务端渲染。
## [响应式UI](https://material-ui.com/zh/guides/responsive-ui/)
> Material-UI布局，使用统一的组件和间距，实现了多平台、多环境和屏幕尺寸的统一性
### [Grid 组件](https://material-ui.com/layout/grid/)
> Material-UI的响应式UI，是基于12列的栅格布局。Material-UI的栅格系统是由 Grid 组件实现的，它使用了 CSS 弹性盒模型，它有两种类型的布局，分别是 containers 和 items。item的宽度被设置为百分比，因此它们总是基于父元素而流动、动态地变换大小。items使用内边距padding生成元素之间的间距空间。

> Material-UI栅格系统支持五种断点模式，分别是 xs / sm / md / lg / xl 。每个断点（一个键）匹配一个固定的屏幕宽度（一个值）：
```
1. xs, 特别小的屏幕，0px or larger
2. sm, 小屏幕，600px or larger
3. md, 中等屏幕，960px or larger
4. lg, 大屏幕， 1280px or larger
5. xl, 超大屏幕， 1920px or larger



value         |0px     600px    960px    1280px   1920px
key           |xs      sm       md       lg       xl
screen width  |--------|--------|--------|--------|-------->
range         |   xs   |   sm   |   md   |   lg   |   xl
```
### [Hidden](https://material-ui.com/layout/hidden/)
> Hidden组件用于隐藏任何内容，它可以结合Grid / Breakpoints组件一起使用。它的实现原理是，基于breakpoints进行显示与隐藏。
 ![workes](https://upload-images.jianshu.io/upload_images/2463290-ae49640baf4087a2.png)
#### 示例
```
        <Hidden xsUp>
          <Paper className={classes.paper}>xsUp</Paper>
        </Hidden>
        <Hidden smUp>
          <Paper className={classes.paper}>smUp</Paper>
        </Hidden>
        <Hidden mdUp>
          <Paper className={classes.paper}>mdUp</Paper>
        </Hidden>
        <Hidden lgUp>
          <Paper className={classes.paper}>lgUp</Paper>
        </Hidden>
        <Hidden xlUp>
          <Paper className={classes.paper}>xlUp</Paper>
        </Hidden>
```
### [Breakpoints 组件](https://material-ui.com/layout/breakpoints/)
> 一个 breakpoint 就是一组预定义的屏幕尺寸范围，它决定了特定了布局需求。为了最适宜的用户体验，material design要实现多屏幕适配。Material-UI对material design规范进行了简化实现。每一个breakpoint都会匹配一定范围的屏幕尺寸。
```
1. xs, 特别小的屏幕，0px or larger
2. sm, 小屏幕，600px or larger
3. md, 中等屏幕，960px or larger
4. lg, 大屏幕， 1280px or larger
5. xl, 超大屏幕， 1920px or larger



value         |0px     600px    960px    1280px   1920px
key           |xs      sm       md       lg       xl
screen width  |--------|--------|--------|--------|-------->
range         |   xs   |   sm   |   md   |   lg   |   xl
```
这些值可以自定义。 这些值被用于主题设定，你可以在 [breakpoints.values](https://material-ui.com/zh/customization/default-theme/?expand-path=$.breakpoints.values) 对象上找到它们。
#### 定义断点
```
const values = {
  xs: 0,
  sm: 600,
  md: 960,
  lg: 1280,
  xl: 1920,
};

const theme = {
  breakpoints: {
    keys: ['xs', 'sm', 'md', 'lg', 'xl'],
    up: key => `@media (min-width:${values[key]}px)`,
  },
};
```
#### CSS媒体查询
CSS媒体查询是使UI响应的惯用方法。该主题提供了四种样式助手

* [theme.breakpoints.up(key)](https://material-ui.com/zh/customization/breakpoints/#theme-breakpoints-up-key-media-query)
* [theme.breakpoints.down(key)](https://material-ui.com/zh/customization/breakpoints/#theme-breakpoints-down-key-media-query)
* [theme.breakpoints.only(key)](https://material-ui.com/zh/customization/breakpoints/#theme-breakpoints-only-key-media-query)
* [theme.breakpoints.between(start, end)](https://material-ui.com/zh/customization/breakpoints/#theme-breakpoints-only-key-media-query)
```
const styles = theme => ({
  root: {
    padding: theme.spacing(1),
    [theme.breakpoints.down('sm')]: {
      backgroundColor: theme.palette.secondary.main,
    },
    [theme.breakpoints.up('md')]: {
      backgroundColor: theme.palette.primary.main,
    },
    [theme.breakpoints.up('lg')]: {
      backgroundColor: green[500],
    },
  },
});
```
#### JavaScript媒体查询
有时, 使用 CSS 是不够的。 您可能希望基于 JavaScript 中的断点值更改 React 渲染树。
##### [useMediaQuery](https://material-ui.com/zh/components/use-media-query/)
   这是React的CSS媒体查询钩子。 它侦听与CSS媒体查询的匹配。 它允许根据查询是否匹配来呈现组件。
```
import React from 'react';
import useMediaQuery from '@material-ui/core/useMediaQuery';

export default function SimpleMediaQuery() {
  const matches = useMediaQuery('(min-width:600px)');

  return <span>{`(min-width:600px) matches: ${matches}`}</span>;
}
```
##### withWidth() 高级组件
```
import withWidth from '@material-ui/core/withWidth';

function MyComponent(props) {
  return <div>{`Current width: ${props.width}`}</div>;
}

export default withWidth()(MyComponent);
```