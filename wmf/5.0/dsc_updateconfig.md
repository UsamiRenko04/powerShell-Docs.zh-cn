---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677469"
---
# <a name="on-demand-pull-of-dsc-configurations"></a>DSC 配置的按需请求

新的 Update-DscConfiguration cmdlet 将触发对元配置中所定义请求服务器的请求。 该行为通常称为“立即请求”。


一旦触发，请求的行为将与以正常频率触发的行为完全相同：

1. 将当前配置的校验和与请求服务器上配置的校验和相比较。
2. 如果它们相同，则不应用配置而成功完成操作。
3. 如果它们不同，则从请求服务器请求并应用配置。

**注意：** 如果元配置 RefreshMode = 'Push'，则此 cmdlet 将返回错误，从而当目标节点为“请求”模式时，此 cmdlet 将始终不执行任何操作。

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
