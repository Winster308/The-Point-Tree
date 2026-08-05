# 基础层级解析

这是一个相对简洁的层级，功能较少。大多数功能需要额外添加。

```js
addLayer("p", {
    startData() { return {                  // startData 是一个返回该层级默认数据的函数。
        unlocked: true,                     // 你可以在此添加更多变量，以将它们加入你的层级。
        points: new Decimal(0),             // "points" 是该层级主要资源的内部名称。
    }},

    color: "#4BDC13",                       // 该层级的颜色，会影响多个元素。
    resource: "prestige points",            // 该层级主要声望资源的名称。
    row: 0,                                 // 该层级所在的行（0 为第一行）。

    baseResource: "points",                 // 你的声望获取所基于的资源的名称。
    baseAmount() { return player.points },  // 一个函数，用于返回 baseResource 的当前数量。

    requires: new Decimal(10),              // 获得 1 点声望货币所需的基础资源数量。
                                            // 同时也是解锁该层级所需的数量。

    type: "normal",                         // 决定用于计算声望货币的公式。
    exponent: 0.5,                          // "normal" 类型的声望获取公式为（货币^指数）。

    gainMult() {                            // 返回你对声望资源获取量的倍数。
        return new Decimal(1)               // 在此处加入任何影响获取量的加成。
    },
    gainExp() {                             // 返回你对声望资源获取量的指数。
        return new Decimal(1)
    },

    layerShown() { return true },          // 返回一个布尔值，决定该层级的节点是否应在树中显示。

    upgrades: {
        // 查看升级文档以了解此处应填写的内容！
    },
})
```