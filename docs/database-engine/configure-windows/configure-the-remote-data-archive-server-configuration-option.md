---
title: "remote data archive サーバー構成オプションの構成 | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3a44b337e360d93aa5e9b66d7b23aeee9ba9175
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>remote data archive サーバー構成オプションの構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **remote data archive** オプションを使用して、サーバー上のデータベースやテーブルを Stretch に対して有効にできるかどうかを指定します。 詳細については、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
 **remote data archive** には次の値を指定できます。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|0|サーバー上のデータベースとテーブルを Stretch に対して有効にできません。|  
|@shouldalert|サーバー上のデータベースとテーブルを Stretch に対して有効にできます。|  
  
 **sp_configure** を実行して **remote data archive** オプションの値を設定するには、sysadmin または serveradmin の権限が必要です。  
  
## <a name="example"></a>例  
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
  
## <a name="see-also"></a>参照  
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
