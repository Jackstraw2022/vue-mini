# 简介

::: tip 注意
阅读本文档前请先阅读[小程序开发文档](https://developers.weixin.qq.com/miniprogram/dev/framework/)以及 [Vue.js 文档](https://cn.vuejs.org)，本文档将不再重复它们已有的内容。
:::

Vue Mini 是一个基于 Vue 3 的小程序框架，它能让你用组合式 API 写小程序。与某些小程序开发方案不同的是 Vue Mini 核心仅仅是一个轻量的运行时库，它既不依赖任何编译步骤，也不涉及任何 Virtual DOM。并且 Vue Mini 从一开始就被设计为能跟小程序原生语法协同工作，你甚至能在同一个页面或组件内混用原生语法与 Vue Mini，这能让你很轻松的将其整合进既有项目中。当然，你也能完全使用 Vue Mini 开发一个小程序。

Vue Mini 仅聚焦于小程序逻辑部分，也就是 JS 部分，它并不影响小程序的模版、样式及配置。

## 动机

Vue 3 之所以提出组合式 API 是为了解决：逻辑复用、复杂代码组织以及更好的 TypeScript 支持这三大问题。而小程序也有这些问题，并且小程序没有响应式数据，每次更新数据需要调用 `setData`。Vue 的响应式数据 + 组合式 API 能非常好的解决这些问题，于是就有了 Vue Mini。

## 它是如何工作的？

Vue Mini 底层直接依赖于 [@vue/reactivity](https://github.com/vuejs/vue-next/tree/master/packages/reactivity)，它是 Vue 3 的响应式核心。事实上，你可以简单的将 Vue Mini 理解为 @vue/reactivity 与小程序的绑定。它会在适当的时机调用 `setup` 函数，并监听返回的响应式数据，如果数据变化了，就调用 `setData` 通知小程序。如果返回的是方法，就将其添加到小程序上。如果你在 `setup` 函数内调用生命周期钩子函数，Vue Mini 也会将其动态注入到小程序上。

## 支持的平台

目前 Vue Mini 仅支持微信小程序。虽然技术上 Vue Mini 可以支持其他小程序平台，但由于时间跟精力的限制，短期内并没有这样的计划。未来一段时间 Vue Mini 仍然只会专注于微信小程序，持续提升微信小程序的 UX 以及 DX。
