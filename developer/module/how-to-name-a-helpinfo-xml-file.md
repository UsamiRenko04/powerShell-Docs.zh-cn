---
title: 如何命名 HelpInfo XML 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857823"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>如何命名 HelpInfo XML 文件

本主题介绍了可更新帮助信息文件，通常称为 HelpInfo XML 文件的所需的名称格式。

## <a name="how-to-name-a-helpinfo-xml-file"></a>如何命名 HelpInfo XML 文件

HelpInfo XML 文件必须具有以下格式的名称。

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

名称的元素如下所示。

ModuleName 值的**名称**的属性**ModuleInfo**对象[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将返回。
值**名称**的属性**ModuleInfo**对象[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将返回。

ModuleGUID 值的**GUID**密钥模块清单中。

例如，如果模块名称为"TestModule"，模块 GUID 为 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，则该模块的 HelpInfo XML 文件的名称将为：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`