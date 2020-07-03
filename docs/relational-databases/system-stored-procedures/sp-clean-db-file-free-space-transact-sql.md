---
title: sp_clean_db_file_free_space (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_file_free_space
- sp_clean_db_file_free_space_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ghost records
- sp_clean_db_file_free_space
ms.assetid: 3eb53a67-969d-4cb8-9681-b1c8e6fd55b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9f137b52e04d73cb99b30319cac8f1f34137f681
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85871266"
---
# <a name="sp_clean_db_file_free_space-transact-sql"></a>sp_clean_db_file_free_space (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ変更ルーチンのためにデータベース ページに残った残存情報を削除します。 sp_clean_db_file_free_space は、データベースの1つのファイルについてのみ、すべてのページをクリーニングします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_clean_db_file_free_space   
[ @dbname ] = 'database_name'   
, @fileid = 'file_number'   
 [ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>引数  
 [ @dbname =] '*database_name*'  
 クリーニングするデータベースの名前です。 *dbname*は**sysname**であり、NULL にすることはできません。  
  
 [ @fileid =] '*file_number*'  
 クリーニングするデータファイルの id を示します。 *file_number*は**int**であり、NULL にすることはできません。  
  
 [ @cleaning_delay =] '*delay_in_seconds*'  
 ページをクリーニングする間隔を指定します。 これにより、i/o システムへの影響が軽減されます。 *delay_in_seconds*は**int**で、既定値は0です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 行への参照を削除することにより、行の移動を発生させるテーブルまたは更新操作の操作を削除できます。 ただし、特定の状況下では、行がゴースト レコードとして、物理的にデータ ページ上に残ってしまう場合があります。 ゴーストレコードは、バックグラウンドプロセスによって定期的に削除されます。 この残存データは、クエリへの応答としてによって返されることはありません [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。 ただし、データまたはバックアップ ファイルの物理的なセキュリティに不安があるような環境では、sp_clean_db_file_free_space を使用することで、これらのゴースト レコードをクリーニングすることができます。  
  
 sp_clean_db_file_free_space の実行にかかる時間は、ファイルのサイズ、使用可能な空き領域、および、ディスク容量によって異なります。 sp_clean_db_file_free_space プロシージャは、I/O アクティビティに著しく影響する場合があるため、通常の業務時間を避けて実行することをお勧めします。  
  
 sp_clean_db_file_free_space を実行する前に、データベースの完全バックアップを作成することをお勧めします。  
  
 関連する[sp_clean_db_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md)ストアドプロシージャは、データベース内のすべてのファイルをクリーンアップします。  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、データベースのプライマリデータファイルから残存情報をすべて消去し `AdventureWorks2012` ます。  
  
```  
USE master;  
GO  
EXEC sp_clean_db_file_free_space   
@dbname = N'AdventureWorks2012', @fileid = 1 ;  
```  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)
 <br>[ゴーストクリーンアッププロセスガイド](../ghost-record-cleanup-process-guide.md) 
  
  
