---
title: DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: c2dd0389f4ec3287fbe23875458ab5d34ef269f7
ms.sourcegitcommit: 79e6d49ae4632f282483b0be935fdee038f69cc2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2019
ms.locfileid: "72174657"
---
# <a name="dbcc-showresultcachespaceused-transact-sql"></a>DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Azure [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] データベースの記憶域スペースで使用されている結果セットのキャッシュが表示されます。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC SHOWRESULTCACHESPACEUSED  
[;]  
```  
## <a name="remarks"></a>Remarks

`DBCC SHOWRESULTCACHESPACEUSED` コマンドは、パラメーターがなく、このコマンドを実行したデータベースで使用されるスペースが返されます。

結果セットのキャッシュの最大サイズは、データベースあたり 1 TB です。  Azure SQL Data Warehouse では、結果セットのキャッシュ内のエントリが以下の条件で自動的に削除されます。

- 結果セットが使用されていない場合は、48 時間ごと。
- 結果セットのキャッシュが最大サイズに接近した場合。

データベースの結果セット キャッシュを手動で空にするには、次のいずれかのオプションを使用します。

- データベースの結果セット キャッシュ機能を無効にする
- データベースに接続した状態で `DBCC DROPRESULTSETCACHE` を実行する 

データベースを一時停止しても、結果セットのキャッシュは空になりません。  

## <a name="permissions"></a>アクセス許可

VIEW SERVER STATE 権限が必要です。
  
## <a name="result-sets"></a>結果セット  
  
|[列]|データ型|[説明]|  
|------------|---------------|-----------------|  
|reserved_space|BIGINT|データベースに使用されている合計領域 (KB 単位)。 この数値は、キャッシュされた結果セットの増加に応じて変化します。|  
|data_space|BIGINT|データに使用されている領域 (KB 単位)。|  
|index_space|BIGINT|インデックスに使用されている領域 (KB 単位)。|  
|unused_space|BIGINT|予約済み領域の一部で使用されていない領域 (KB 単位)。|  


## <a name="see-also"></a>参照

[ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)</br>
[SET RESULT SET CACHING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-result-set-caching-transact-sql)</br>
[DBCC DROPRESULTSETCACHE  &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)