---
title: "Agent XP サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 34863e78d2210b8c5860258dd5ade1f7aeb241c2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="agent-xps-server-configuration-option"></a>Agent XP サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Agent XPs** オプションは、このサーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを有効にする場合に使用します。 このオプションを有効にしないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオブジェクト エクスプローラーに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] エージェントのノードが表示されません。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ツールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを開始すると、これらの拡張ストアド プロシージャは自動的に有効になります。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のオブジェクト エクスプローラーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスの状態にかかわらず、これらの拡張ストアド プロシージャを有効にしない限り、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのノードのコンテンツは表示されません。  
  
 可能な値は次のとおりです。  
  
-   **0**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを使用できないことを示します (既定)。  
  
-   **1**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを使用できることを示します。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
## <a name="example"></a>例
 次の例では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを有効にします。  

1. Microsoft SQL Server Management Studio から、データベース エンジンに接続します。

2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。

3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 
  
```tsql 
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>参照  
 [管理タスクの自動化 &#40;SQL Server エージェント&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [SQL Server エージェント サービスの開始、停止、または一時停止](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  

