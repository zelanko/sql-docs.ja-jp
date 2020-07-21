---
title: remote data archive サーバー構成オプションの構成 | Microsoft Docs
description: SQL Server で remote data archive オプションを使用して、サーバー上のデータベースやテーブルを Stretch に対して有効にできるかどうかを指定する方法について説明します。
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
ms.openlocfilehash: fc53b5392d6bd493b634e9e2c8a4a92613eb8c32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785745"
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>remote data archive サーバー構成オプションの構成
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **remote data archive** オプションを使用して、サーバー上のデータベースやテーブルを Stretch に対して有効にできるかどうかを指定します。 詳細については、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
 **remote data archive** には次の値を指定できます。  
  
|値|説明|  
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
  
  
