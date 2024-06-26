# 开发注意事项

## 图表的宽高

图表的默认宽高都是`100%`，相对于它的父容器。

因此，你可以用一个**已有宽高**的容器来包裹图表，比如：`<div class="container"><lazy-bar></lazy-bar></div>`。

也可以直接用`style`设置图表的宽高，比如：`<lazy-bar style="width: 300px; height: 20rem"></lazy-bar>`

## 环境差异

各大主流框架虽然对 Web Component 做了很好的支撑，但不同框架不同版本还有一些差异

### 1. 传参问题

图表组件的所有 Prop 都设计为 DOM 的 Property 而不是 Attribute，在 Vue2 中，需要`.prop`显式修饰一下才行；而在 Vue3 中可以自动判断。

#### Vue2

`<lc-line :source.prop="arr"></lc-line>`

#### Vue3

`<lc-line :source="arr"></lc-line>`

### 2. 构建问题

Vue2 不识别的标签默认就认为是自定义元素；而 Vue3 使用 Vite 构建时，需要显式排除，不让构建。

#### Vue2

无需额外配置

#### Vue3

::: code-group

```js [vite.config.js]
export default {
  ...,
  vue: {
    template: {
      compilerOptions: {
        // 将所有前缀为 lc- 的标签名都视为自定义元素
        isCustomElement: (tag) => tag.startsWith('lc-'),
      },
    },
  },
}
```

:::
