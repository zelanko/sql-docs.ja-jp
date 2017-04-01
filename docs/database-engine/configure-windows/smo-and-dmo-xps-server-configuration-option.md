---
title: "SMO and DMO XPs サーバー構成オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# SMO and DMO XPs サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このサーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) の拡張ストアド プロシージャを使用するには、SMO and DMO XPs オプションを使用します。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] の DMO は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で削除されました。  
  
 次の表に、このオプションで使用可能な値を示します。  
  
|値|意味|  
|-----------|-------------|  
|0|SMO 拡張ストアド プロシージャ (XP) を使用できません。|  
|1|SMO 拡張ストアド プロシージャ (XP) を使用できます。 これは既定値です。|  
  
 この設定はすぐに有効になります。  
  
## 使用例  
 次の例では、SMO の拡張ストアド プロシージャを有効にします。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## 参照  
 [SQL Server 管理オブジェクト &#40;SMO&#41; プログラミング ガイド](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  