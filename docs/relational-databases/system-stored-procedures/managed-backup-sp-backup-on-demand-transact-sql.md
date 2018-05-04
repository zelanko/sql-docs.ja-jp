---
title: managed_backup.sp_backup_on_demand (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
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
ms.openlocfilehash: cb3620bc20ae46dd2aac4fa89d4031ab996ed0b1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="managedbackupspbackupondemand-transact-sql"></a>managed_backup.sp_backup_on_demand (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  要求[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を指定されたデータベースのバックアップを実行します。  
  
 このストアド プロシージャを使用すると、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]で構成されるデータベースに対してアドホック バックアップを実行できます。 これにより、バックアップのチェーンが中断し、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]プロセスは認識し、バックアップは同じ Windows Azure Blob ストレージ コンテナーに格納します。  
  
 バックアップが正常に完了すると、バックアップ ファイルの完全なパスが返されます。 これには、バックアップ操作の結果として作成された新しいバックアップ ファイルの名前と場所が含まれます。  
  
 場合、エラーが返されます[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]のバックアップを実行中は、型指定されたデータベースを指定します。 この場合、返されるエラー メッセージには、現在のバックアップのアップロード先となるバックアップ ファイルの完全なパスが含まれます。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="Arguments"></a> 引数  
 @database_name  
 バックアップの実行対象となるデータベースの名前。 @database_nameは**SYSNAME**です。  
  
 @type  
 実行するバックアップの種類: Database または Log。 @typeパラメーターは**nvarchar (32)** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 メンバーシップが必要**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および**EXECUTE**に対するアクセス許可**sp_deletebackuphistory**ストアド プロシージャです。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース "TestDB" に対してデータベース バックアップを要求します。 このデータベースでは[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]有効にします。  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 各コードでは、言語属性フィールドで "tsql" を選択します。  
  
  
