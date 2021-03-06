---
title: 使用 Visual Studio Code 进行远程编辑和调试
description: 使用 Visual Studio Code 进行远程编辑和调试
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655573"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>使用 Visual Studio Code 进行远程编辑和调试

对于您已熟悉 ISE，您可能记得，可以运行`psedit file.ps1`从打开的文件-本地或远程的集成控制台右键在 ISE 中。

事实证明，此功能也是适用于 VSCode 的 PowerShell 扩展中可用。 本指南将演示如何执行此操作。

## <a name="prerequisites"></a>必备条件

本指南假定你拥有：

- 远程资源 (例如： 虚拟机，容器) 有权访问
- 它和主机计算机上运行的 PowerShell
- VSCode 和适用于 VSCode 的 PowerShell 扩展

此功能适用于 Windows PowerShell 和 PowerShell Core。

连接到远程计算机通过 WinRM、 PowerShell Direct 或 SSH 时，此功能也适用。 如果你想要使用 SSH，但使用的 Windows，请查看[Win32 版本的 SSH](https://github.com/PowerShell/Win32-OpenSSH)！

## <a name="lets-go"></a>开始

在本部分中，我将逐步远程编辑和调试从我正在 MacBook Pro，到 Ubuntu VM 在 Azure 中运行。 我可能没有使用 Windows，但**的过程是相同**。

### <a name="local-file-editing-with-open-editorfile"></a>使用打开 EditorFile 进行编辑的本地文件

使用 PowerShell 扩展启动 VSCode 并打开 PowerShell 控制台中集成，我们可以键入`Open-EditorFile foo.ps1`或`psedit foo.ps1`以在编辑器中打开本地 foo.ps1 文件权限。

![打开 EditorFile foo.ps1 可在本地工作](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 必须已存在。

在这里，我们可以：

将断点添加到滚动条槽![添加断点，以线](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

并按 F5 调试 PowerShell 脚本。
![调试 PowerShell 本地脚本](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

调试时，可以使用调试控制台进行交互，请查看左侧和调试工具的所有其他标准中的作用域中的变量。

### <a name="remote-file-editing-with-open-editorfile"></a>使用打开 EditorFile 进行编辑的远程文件

现在让我们将放入远程文件编辑和调试。 步骤都几乎相同，只是一件事我们需要先做-我们的 PowerShell 会话输入到远程服务器。

没有为 cmdlet 来执行此操作。 它称为`Enter-PSSession`。

该 cmdlet 的已关闭说明是：

- `Enter-PSSession -ComputerName foo` 启动 WinRM 通过会话
- `Enter-PSSession -ContainerId foo` 和`Enter-PSSession -VmId foo`开始通过 PowerShell Direct 会话
- `Enter-PSSession -HostName foo` 启动通过 SSH 会话

有关详细信息`Enter-PSSession`，签出文档[此处](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6)。

我将使用 SSH 远程处理由于我从 macOS 将在 Azure 中的 Ubuntu VM。

首先，在集成的控制台中，让我们运行我们 Enter-pssession。 您将知道由于是在会话中`[something]`会显示在提示符下的左侧。

![Enter-pssession 调用](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

在这里，我们可以像我们所编辑的本地脚本执行的确切步骤。

1. 运行`Open-EditorFile test.ps1`或`psedit test.ps1`若要打开远程`test.ps1`文件![打开 EditorFile test.ps1 文件](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. 编辑文件/设置断点 ![编辑并设置断点](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. 启动调试 (F5) 该远程文件

![调试远程文件](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

这就是一切就这么简单 ！ 我们希望本指南帮助清除了有关远程调试和编辑 PowerShell 在 VSCode 中的任何问题。

如果有任何疑问，欢迎您随时打开问题[GitHub 存储库上](http://github.com/powershell/vscode-powershell)。
