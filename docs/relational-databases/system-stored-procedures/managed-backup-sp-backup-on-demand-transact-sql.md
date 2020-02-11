---
title: managed_backup。 sp_backup_on_demand (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e34cf20585ea7dcd3690d80ee415fc274bf852ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "70155399"
---
# <a name="managed_backupsp_backup_on_demand-transact-sql"></a>managed_backup。 sp_backup_on_demand (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]されたデータベースのバックアップを実行するように要求します。  
  
 このストアド プロシージャを使用すると、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]で構成されるデータベースに対してアドホック バックアップを実行できます。 これにより、バックアップチェーンと[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]プロセスの中断が認識され、バックアップが同じ Azure Blob ストレージコンテナーに格納されます。  
  
 バックアップが正常に完了すると、完全バックアップファイルのパスが返されます。 これには、バックアップ操作の結果として生成される新しいバックアップファイルの名前と場所が含まれます。  
  
 が指定された[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]データベースの指定された種類のバックアップを実行中の場合、エラーが返されます。 この場合、返されるエラー メッセージには、現在のバックアップのアップロード先となるバックアップ ファイルの完全なパスが含まれます。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="Arguments"></a>数値  
 @database_name  
 バックアップを実行するデータベースの名前を指定します。 @database_nameは**SYSNAME**です。  
  
 @type  
 実行するバックアップの種類: Database または Log。 @typeパラメーターは**NVARCHAR (32)** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 **Db_backupoperator**データベースロールのメンバーシップ、 **ALTER ANY CREDENTIAL**権限、および**Sp_delete_backuphistory**ストアドプロシージャに対する**EXECUTE**権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、データベース ' TestDB ' のデータベースバックアップ要求を作成します。 このデータベースは[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]有効になっています。  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 各コードでは、言語属性フィールドで "tsql" を選択します。  
  
  
