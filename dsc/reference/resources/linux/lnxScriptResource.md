---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxScript 资源
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047138"
---
# <a name="dsc-for-linux-nxscript-resource"></a>适用于 Linux 的 DSC nxScript 资源

PowerShell Desired State Configuration (DSC) 中的 **nxScript** 资源提供了在 Linux 节点上运行 Linux 脚本的机制。

## <a name="syntax"></a>语法

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>“属性”

|  属性 |  说明 |
|---|---|
| GetScript| 提供调用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet 时运行的脚本。 该脚本必须以 shebang 开头，如 #!/bin/bash。|
| SetScript| 提供脚本。 调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 时，将首先运行 **TestScript**。 如果 **TestScript** 块返回非 0 退出代码，则将运行 **SetScript** 块。 如果 **TestScript** 返回退出代码 0，则将不运行 **SetScript**。 该脚本必须以 shebang 开头，如 `#!/bin/bash`。|
| TestScript| 提供脚本。 调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 时，将运行此脚本。 如果它返回非 0 退出代码，则将运行 SetScript。 如果它返回退出代码 0，则将不运行 **SetScript**。 调用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet 时，也会运行 **TestScript**。 但是，在这种情况下，无论从 **TestScript** 返回何种退出代码，都不会运行 **SetScript**。 如果实际配置与当前所需状态配置相匹配，则 **TestScript** 必定返回退出代码 0；如两者不匹配，则返回非 0 退出代码。 （当前所需状态配置是在使用 DSC 的节点上执行的最后一个配置）。 该脚本必须以 shebang 开头，如 1#!/bin/bash.1|
| 用户| 将该脚本作为此用户运行。|
| 组| 将该脚本作为此组运行。|
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|

## <a name="example"></a>示例

以下示例演示了如何使用 **nxScript** 资源进行其他配置管理。

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```