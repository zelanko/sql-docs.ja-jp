---
title: sys.sp_cleanup_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 111986a771b9cfb156c0d37688565b39401411f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037231"
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>sys.sp_cleanup_temporal_history (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

1 つのトランザクション内で構成された HISTORY_RETENTION 期間に一致するテンポラル履歴テーブルからすべての行を削除します。
  
## <a name="syntax"></a>構文  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>引数  

*@table_name*

どの保有期間のクリーンアップが呼び出される、テンポラル テーブルの名前。

*schema_name*

現在のテンポラル テーブルが属するスキーマの名前

*row_count_var* [OUTPUT]

削除された行の数を返す出力パラメーター。 このパラメーターを返すはかどうかは、履歴テーブルに列ストア インデックスがクラスター化されたが、常に 0 です。
  
## <a name="remarks"></a>コメント
このストアド プロシージャは、有限のリテンション期間を指定することテンポラル テーブルでのみ使用できます。
すぐに、履歴テーブルからすべての期限切れの行をクリーンアップする必要がある場合にのみ、このストアド プロシージャを使用します。 おく必要があります、同じトランザクション内のすべての対象となる行を削除するようにデータベース ログや I/O サブシステムに大きく影響ことができます。 

常に、期限切れの一般的なデータベースと通常のワークロードに対する影響を最小限に行を削除するクリーンアップでは、内部のバック グラウンド タスクに依存することをお勧めします。

## <a name="permissions"></a>アクセス許可  
 Db_owner アクセス許可が必要です。  

## <a name="example"></a>例

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>関連項目

[テンポラル テーブルの保有ポリシー](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
