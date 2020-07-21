---
title: Ole Automation Procedures サーバー構成オプション | Microsoft Docs
description: "\"Ole Automation Procedures\" オプションについて説明します。 これによって、SQL Server が Transact-SQL バッチ内の OLE オートメーションオブジェクトをインスタンス化できるかどうかを指定する方法について説明します。"
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5390fce7517b56ea26a33392a72da7cb39dcd34d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773687"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>Ole Automation Procedures サーバー構成オプション
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **Ole Automation Procedures** オプションは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内で OLE オートメーション オブジェクトをインスタンス化するかどうかを指定するために使用します。 このオプションは、ポリシー ベースの管理または **sp_configure** ストアド プロシージャを使用して構成することもできます。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
 **Ole Automation Procedures** オプションに設定できる値を次に示します。  
  
 0  
 OLE オートメーション プロシージャを無効にします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいインスタンスの既定値です。  
  
 1  
 OLE オートメーション プロシージャを有効にします。  
  
 OLE オートメーション プロシージャが有効である場合、 **sp_OACreate** を呼び出すと OLE 共有実行環境が開始します。  
  
 **Ole Automation Procedures** オプションの現在の値は、 **sp_configure** システム ストアド プロシージャを使用して確認および変更できます。  
  
## <a name="examples"></a>例  
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
  
  
