---
title: remote data archive サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
author: rothja
ms.author: jroth
manager: jroth
ms.openlocfilehash: 39967c68efa3f514759c3c7c910674f62097e3ce
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66783863"
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>remote data archive サーバー構成オプションの構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **remote data archive** オプションを使用して、サーバー上のデータベースやテーブルを Stretch に対して有効にできるかどうかを指定します。 詳細については、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
 **remote data archive** には次の値を指定できます。  
  
|[値]|Description|  
|-----------|-----------------|  
|0|サーバー上のデータベースとテーブルを Stretch に対して有効にできません。|  
|1|サーバー上のデータベースとテーブルを Stretch に対して有効にできます。|  
  
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
  
  
