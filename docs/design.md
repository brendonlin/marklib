# Design

## 需求

### 一期需求

- 更好地管理浏览器收藏页面。以存在 200 个以上的收藏地址为前提。
- 能够基于域名进行管理，包括子域名。
- 能够对地址进行标签添加，可以基于标签进行筛选

### 未来需求

- 每个地址会记录其点击数量，方便清理不常使用的地址。
- 可以根据相互点击的历史记录绘制出一个类似地图的阿

## 界面设计

功能点：

- 根据域名查看标签，默认模式
- 根据标签筛选标签
- 在单页上可以查看所有标签
- 操作
  - 导入标签
  - 标签的增删改查
  - 点击标签跳转
- 因为需要记录点击数据、标签添加，因此需要一个后端服务。用户认证也建议做掉，就简单一些。

## 数据设计

一个标签的数据形式

```json
{
    address:
    title:
    host:
    labels:
    clicks:
    last_modified:
    created:
}
```

## 程序设计

- 建议前端负责主要的过滤、排序、层级构建。
- 前端自行基于基础数据构建树形的索引，注意不需要修改源数据结构，只需要建立一个索引即可
