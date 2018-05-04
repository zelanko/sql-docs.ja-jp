---
title: sys.sp_cleanup_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.service: sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
caps.latest.revision: 4
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ebea6e162bb047f6c6224001e70dede74b5d58cc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>sys.sp_cleanup_temporal_history (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

1 つのトランザクション内で構成された HISTORY_RETENTION 期間に一致する一時的な履歴テーブルからすべての行を削除します。
  
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

削除された行の数を返す出力パラメーター。 このパラメーターを返すはかどうか、履歴テーブルには、列ストア インデックスがクラスター化されたが、常に 0 です。
  
## <a name="remarks"></a>解説
このストアド プロシージャは、有限の保有期間を指定いるテンポラル テーブルでのみ使用できます。
履歴テーブルからすべての期限切れの行をすぐにクリーンアップする必要がある場合にのみ、このストアド プロシージャを使用します。 同じトランザクション内のすべての対象となる行を削除するようにデータベースのログ、I/O サブシステムに大きく影響を持つことができますを知る必要があります。 

常に、期限切れの通常の作業負荷と一般的なデータベースで最小限の影響を含む行を削除ことクリーンアップでは、内部のバック グラウンド タスクに依存することをお勧めします。

## <a name="permissions"></a>権限  
 Db_owner アクセス許可が必要です。  

## <a name="example"></a>例

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>参照

[テンポラル テーブルの保有ポリシー](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
