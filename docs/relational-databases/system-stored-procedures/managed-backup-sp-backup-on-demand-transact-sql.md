---
title: managed_backup.sp_backup_on_demand (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- smart_admin.sp_backup_on_demand
- smart_admin.sp_backup_on_demand_TSQL
- sp_backup_on_demand_TSQL
- sp_backup_on_demand
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.sp_backup_on_demand
- sp_backup_on_demand
ms.assetid: 638f809f-27fa-4c44-a549-9cf37ecc920c
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d95bdd7fa337598c289aaa7a958c33513eec12d0
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38058040"
---
# <a name="managedbackupspbackupondemand-transact-sql"></a>managed_backup.sp_backup_on_demand (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  要求[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を指定されたデータベースのバックアップを実行します。  
  
 このストアド プロシージャを使用すると、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]で構成されるデータベースに対してアドホック バックアップを実行できます。 こうことで、バックアップ チェーンが中断し、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]プロセスは認識し、バックアップは同じ Windows Azure Blob ストレージ コンテナーに格納します。  
  
 バックアップが正常に完了すると、バックアップ ファイルの完全なパスが返されます。 これには、バックアップ操作の結果として作成された新しいバックアップ ファイルの名前と場所が含まれます。  
  
 場合、エラーが返されます[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]のバックアップを実行中は、指定されたデータベースの型を指定します。 この場合、返されるエラー メッセージには、現在のバックアップのアップロード先となるバックアップ ファイルの完全なパスが含まれます。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="Arguments"></a> 引数  
 @database_name  
 バックアップの実行対象となるデータベースの名前。 @database_nameは**SYSNAME**します。  
  
 @type  
 実行するバックアップの種類: Database または Log。 @typeパラメーターが**nvarchar (32)** します。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および**EXECUTE**に対する**sp_deletebackuphistory**ストアド プロシージャ。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース "TestDB" に対してデータベース バックアップを要求します。 このデータベースでは[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にします。  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 各コードでは、言語属性フィールドで "tsql" を選択します。  
  
  
