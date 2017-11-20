---
title: "Ole Automation Procedures サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a7fc4822969e705f82cf6caa75b893f33e923395
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="ole-automation-procedures-server-configuration-option"></a>Ole Automation Procedures サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **Ole Automation Procedures** オプションは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内で OLE オートメーション オブジェクトをインスタンス化するかどうかを指定するために使用します。 このオプションは、ポリシー ベースの管理または **sp_configure** ストアド プロシージャを使用して構成することもできます。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
 **Ole Automation Procedures** オプションに設定できる値を次に示します。  
  
 0  
 OLE オートメーション プロシージャを無効にします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいインスタンスの既定値です。  
  
 1  
 OLE オートメーション プロシージャを有効にします。  
  
 OLE オートメーション プロシージャが有効である場合、 **sp_OACreate** を呼び出すと OLE 共有実行環境が開始します。  
  
 **Ole Automation Procedures** オプションの現在の値は、 **sp_configure** システム ストアド プロシージャを使用して確認および変更できます。  
  
## <a name="examples"></a>使用例  
 OLE オートメーション プロシージャの現在の設定を確認する方法を次の例に示します。  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 OLE オートメーション プロシージャを有効にする方法を次の例に示します。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [セキュリティ構成](../../relational-databases/security/surface-area-configuration.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  

