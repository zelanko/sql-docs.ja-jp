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
author: stevestein
ms.author: sstein
ms.openlocfilehash: c788d78dac45f2371829bb450ac98c94164d97ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070389"
---
# <a name="sp_clean_db_file_free_space-transact-sql"></a>sp_clean_db_file_free_space (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
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
 [ @dbname= ]'*database_name*'  
 クリーニングするデータベースの名前です。 *dbname*は**sysname**であり、NULL にすることはできません。  
  
 [ @fileid= ]'*file_number*'  
 クリーニングするデータファイルの id を示します。 *file_number*は**int**であり、NULL にすることはできません。  
  
 [ @cleaning_delay= ]'*delay_in_seconds*'  
 ページをクリーニングする間隔を指定します。 これにより、i/o システムへの影響が軽減されます。 *delay_in_seconds*は**int**で、既定値は0です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 行への参照を削除することにより、行の移動を発生させるテーブルまたは更新操作の操作を削除できます。 ただし、特定の状況下では、行がゴースト レコードとして、物理的にデータ ページ上に残ってしまう場合があります。 ゴーストレコードは、バックグラウンドプロセスによって定期的に削除されます。 この残存データは、クエリへの[!INCLUDE[ssDE](../../includes/ssde-md.md)]応答としてによって返されることはありません。 ただし、データまたはバックアップ ファイルの物理的なセキュリティに不安があるような環境では、sp_clean_db_file_free_space を使用することで、これらのゴースト レコードをクリーニングすることができます。  
  
 sp_clean_db_file_free_space の実行にかかる時間は、ファイルのサイズ、使用可能な空き領域、および、ディスク容量によって異なります。 sp_clean_db_file_free_space プロシージャは、I/O アクティビティに著しく影響する場合があるため、通常の業務時間を避けて実行することをお勧めします。  
  
 sp_clean_db_file_free_space を実行する前に、データベースの完全バックアップを作成することをお勧めします。  
  
 関連する[sp_clean_db_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md)ストアドプロシージャは、データベース内のすべてのファイルをクリーンアップします。  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、 `AdventureWorks2012`データベースのプライマリデータファイルから残存情報をすべて消去します。  
  
```  
USE master;  
GO  
EXEC sp_clean_db_file_free_space   
@dbname = N'AdventureWorks2012', @fileid = 1 ;  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)
 <br>[ゴーストクリーンアッププロセスガイド](../ghost-record-cleanup-process-guide.md) 
  
  
