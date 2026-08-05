# 模组树（The Modding Tree）

在模组树中制作游戏，主要涉及在对象上定义参数或函数。如果你没有遵循[入门指南](tutorials/getting-started.md)，你应该从在[mod.js](/js/mod.js)中[设置你的基本模组信息](main-mod-info.md)开始。设置模组ID以确保存档功能正常运作非常重要。

除此之外，添加内容的主要方式是通过创建层级。你可以通过调用`addLayer(layername, layerdata)`来添加新层级。[layers.js](/js/layers.js)中有一个基础层级的示例。它只是一个示例，可以随意删除。你也可以将其作为参考或你自己层级的基础。

你可以通过在浏览器中打开[index.html](/index.html)文件来测试你的模组。

大多数情况下，你不需要深入代码来创建内容，但如果你确实想这样做，也是可以的，例如在[components.js](/js/components.js)中添加新的Vue组件。

模组树使用[break\_eternity.js](https://github.com/Patashu/break_eternity.js)来存储大数值。这意味着许多数字是`Decimal`对象，必须以不同方式处理。例如，你必须使用`new Decimal(x)`来创建`Decimal`值，而不是普通数字（对于更大的数值，x可以是数字或字符串）。你通过调用函数来对它们执行操作。例如，使用`x = x.add(y)`代替`x = x + y`。请记住，这也适用于比较运算符，应改用调用`.gt`、`.gte`、`.lt`、`.lte`、`.eq`和`.neq`函数。有关使用`Decimal`值的更多详细信息，请参阅[break\_eternity.js](https://github.com/Patashu/break_eternity.js)文档。

几乎所有值都可以是常量值或动态值。动态值通过放置一个函数来定义，该函数返回任意给定时间该值应为多少。

所有显示文本都可以使用基本的HTML元素（但你不能在那里使用大多数Vue功能）。

在阅读本文档时，描述功能时将使用以下图例：

- 无标签：这是必需的，如果不包含，游戏可能会崩溃。
- **有时必需**：这可能根据层级中的其他内容而必需。
- **可选**：如果你不打算为该层级使用该功能，可以省略。
- **自动分配**：该值将被自动设置，并覆盖你设置的任何值。
- **已弃用**：不建议使用此功能，因为更新的功能能够以更好、更简单的方式实现相同的效果。

## 目录

### 通用

- [入门指南](tutorials/getting-started.md)：使用Github Desktop设置你自己的代码副本的指南。
- [制作模组](tutorials/making-a-mod.md)：使用TMT制作基础模组的指南。
- [主模组信息](main-mod-info.md)：如何在[mod.js](/js/mod.js)中为你的模组设置通用内容。
- [基础层级分解](basic-layer-breakdown.md)：分解具有最少功能的层级组件。
- [层级功能](layer-features.md)：解释你可以赋予层级的所有不同属性。
- [自定义标签页布局](custom-tab-layouts.md)：一种为你的标签页提供不同布局的可选方式。你甚至可以创建全新的组件来使用。
- [自定义游戏布局](trees-and-tree-customization.md)：你可以移除树标签页，向树中添加按钮和其他内容，甚至像层级标签页一样自定义标签页的布局。
- [更新TMT](tutorials/updating-tmt.md)：使用Github Desktop更新你的模组版本的TMT。
- [其他内容](other.md)：TMT拥有的其他简洁功能，这些功能不足以单独成页。

### 常见组件

- [升级](upgrades.md)：如何为层级创建升级。
- [里程碑](milestones.md)：如何为层级创建里程碑。
- [可购买项](buyables.md)：为你的层级创建可重复购买的升级（可选择使其可重置）。例如，可用于制作增强器或太空建筑。
- [可点击项](clickables.md)：可购买项的更通用变体，适用于任何有时可点击的事物。在这些和可购买项之间，你几乎可以做任何事情。
- [成就](achievements.md)：如何为层级（或整个游戏）创建成就。

### 其他组件和功能

- [挑战](challenges.md)：如何为层级创建挑战。
- [进度条](bars.md)：将一些信息显示为进度条、仪表或类似形式。它们高度可定制，也可以是水平和垂直的。
- [子标签页和微标签页](subtabs-and-microtabs.md)：为你的标签页创建子标签页，以及可以放入标签页内的“微标签页”组件。你甚至可以使用它们将一个层级嵌入另一个层级中！
- [网格](grids.md)：创建一组行为相同但拥有各自数据的按钮。非常适合地图瓦片、物品栏网格等！
- [信息框](infoboxes.md)：包含文本的框，可以显示或隐藏。
- [树](trees-and-tree-customization.md)：制作你自己的树。你也可以制作非层级按钮节点！
- [粒子系统](particles.md)：可用于创建视觉效果粒子，也可以用于创建可交互的事物，如黄金饼干或收藏品。