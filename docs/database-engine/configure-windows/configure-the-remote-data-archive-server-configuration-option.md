---
title: "remote data archive サーバー構成オプションの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# remote data archive サーバー構成オプションの構成
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **remote data archive** オプションを使用して、サーバー上のデータベースやテーブルを Stretch に対して有効にできるかどうかを指定します。 詳細については、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
 **remote data archive** には次の値を指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|0|サーバー上のデータベースとテーブルを Stretch に対して有効にできません。|  
|1|サーバー上のデータベースとテーブルを Stretch に対して有効にできます。|  
  
 **sp_configure** を実行して **remote data archive** オプションの値を設定するには、sysadmin または serveradmin の権限が必要です。  
  
## 例  
 次の例では、最初に **remote data archive** オプションの現在の設定を表示します。 次に、値を 1 に設定することによって **remote data archive** オプションを有効にしています。  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 このオプションを無効にするには、値を 0 に設定します。  
  
## 参照  
 [データベースに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  