---
title: TableControl （格式） 的 TableColumnItems TableColumnItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862413"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem Element for TableColumnItems for TableControl (Format)

定义属性或其值显示在一行的列中的脚本。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 TableControl （格式） 的 TableRowEntries TableControl （格式） TableRowEntry 元素TableControl （格式） 的 TableColumnItems TableControl （格式） TableColumnItem 元素 TableControlEntry TableColumnItems 元素

## <a name="syntax"></a>语法

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`TableColumnItem`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableColumnItem 的对齐方式元素](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|可选元素。<br /><br /> 定义如何显示的行的列中的数据。|
|[TableControl （格式） 的 TableColumnItem 的 FormatString 元素](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|指定用于设置格式的行的列中的数据的格式模式。|
|[TableControl （格式） 的 TableColumnItem PropertyName 元素](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定显示其值的属性的名称。|
|[TableControl （格式） 的 TableColumnItem 的脚本块元素](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定行的列中显示其值的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableControlEntry TableColumnItems 元素](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|定义属性或其值显示的行中的脚本。|

## <a name="remarks"></a>备注

行的每个列中，可以指定一个或多个脚本的属性。 如果不指定了任何子元素，该项目是一个占位符，并不显示任何数据。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例演示`TableColumnItem`显示的值的元素`Status`的属性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableControl （格式） 的 TableColumnItem 的对齐方式元素](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems 元素 （格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl （格式） 的 TableColumnItem 的 FormatString 元素](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl （格式） 的 TableColumnItem PropertyName 元素](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl （格式） 的 TableColumnItem 的脚本块元素](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
