---
title: managed_backup.fn_get_parameter (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_get_parameter_TSQL
- smart_admin.fn_get_parameter
- fn_get_parameter_TSQL
- fn_get_parameter
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_parameter
- smart_admin.fn_get_parameter
ms.assetid: ed94e54d-4516-4806-a8ce-f013d3a04122
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2420c689dff7e344c06a6667c15e08d3d4769872
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047260"
---
# <a name="managedbackupfngetparameter-transact-sql"></a>managed_backup.fn_get_parameter (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  パラメーターと値のペアから成る 0 行、1 行、または複数行を格納したテーブルを返します。  
  
 このストアド プロシージャを使用すると、Smart Admin のすべてまたは特定の構成設定を確認できます。  
  
 パラメーターがまだ構成されていない場合は、この関数は 0 行を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.fn_get_parameter ('parameter_name' | '' | NULL )  
```  
  
##  <a name="Arguments"></a> 引数  
 parameter_name  
 パラメーターの名前。 parameter_name は**nvarchar (128)** します。 この関数の引数として NULL または空の文字列が指定されると、構成されたすべての Smart Admin パラメーターの名前と値のペアが返されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|parameter_name|NVARCHAR(128)|パラメーターの名前。 現在の返されるパラメーターの一覧を次に示します。<br/><br/>**FileRetentionDebugXevent**<br/><br/>**SSMBackup2WADebugXevent**<br/><br/>**SSMBackup2WANotificationEmailIds**<br/><br/>**SSMBackup2WAEnableUserDefinedPolicy**<br/><br/>**SSMBackup2WAEverConfigured**<br/><br/>**StorageOperationDebugXevent**|  
|parameter_value|NVARCHAR(128)|パラメーターの現在設定されている値。|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 この関数に対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、少なくとも 1 回構成されたすべてのパラメーターと、それらの現在の値を返します。  
  
```  
USE MSDB  
GO  
SELECT *   
FROM managed_backup.fn_get_parameter (NULL)  
  
```  
  
 次の例では、エラー通知の受信先として指定された電子メール ID を返します。 行が返されない場合は、この電子メール通知オプションが有効になっていないことを意味します。  
  
```  
USE MSDB  
GO  
SELECT *  
FROM managed_backup.fn_get_parameter ('SSMBackup2WANotficationEmailIds')  
  
```  
  
## <a name="see-also"></a>参照  
 
  [Microsoft Azure への SQL Server マネージド バックアップ](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
