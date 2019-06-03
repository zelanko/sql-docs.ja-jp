---
title: 結果セット キャッシュの設定 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 0b932c1fa3aa8575f8f12ef5f164841788f74c1a
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65948746"
---
# <a name="set-result-set-caching-transact-sql"></a>結果セット キャッシュの設定 (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Azure SQL Data Warehouse でクエリの結果セットをキャッシュする
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文

```
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Remarks  

> [!Note]
> この機能をすべてのリージョンにロールアウトしながら、ご利用にインスタンスにデプロイされたバージョンと、機能の可用性に関する最新の[ Azure SQL DW リリースノート](/azure/sql-data-warehouse/release-notes-10-0-10106-0)を確認してください。
  
このコマンドは、マスター データベースに接続しているときに実行する必要があります。  このデータベースの設定変更はすぐに適用されます。  クエリの結果セットをキャッシュすることでストレージ コストが発生します。 データベースの結果キャッシュを無効にすると、直後に、前に永続させた結果キャッシュが Azure SQL Data Warehouse ストレージから削除されます。 is_result_set_caching_on という名前の新しい列が [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql?view=azure-sqldw-latest) に導入され、データベースの結果キャッシュ設定を示します。  

**[オン]** の場合、このデータベースから返されたクエリの結果セットは Azure SQL Data Warehouse ストレージにキャッシュされます。

**[オフ]** の場合、このデータベースから返されたクエリの結果セットは Azure SQL Data Warehouse ストレージにキャッシュされません。

特定の request_id で [sys.pdw_request_steps](/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql?view=azure-sqldw-latest) を問い合わせることで、クエリを実行した結果、結果キャッシュにデータが見つかるかどうかを確認できます。 キャッシュに該当するデータが見つかる場合、クエリ結果には、次の詳細を含むステップが 1 つ与えられます。

|**列名**|**[オペレーター]**|**Value**|
|----|----|----|
|operation_type|=|ReturnOperation|
|step_index|=|0|
|location_type|=|Control|
|command|Like|%DWResultCacheDb%|
||||
  
## <a name="permissions"></a>アクセス許可

以下のアクセス許可が必要です。

- サーバー レベル プリンシパル ログイン (プロビジョニング処理で作成されたもの) または
- dbmanager データベース ロールのメンバー。

所有者が dbmanager ロールのメンバーである場合を除き、データベースの所有者はデータベースを変更することはできません。
  
## <a name="examples"></a>使用例

### <a name="enable-result-set-caching-for-a-database"></a>データベースに対して結果セットのキャッシュを有効にする

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING ON;
```

### <a name="disable-result-set-caching-for-a-database"></a>データベースに対して結果セットのキャッシュを無効にする

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING OFF;
```

### <a name="check-result-set-caching-setting-for-a-database"></a>データベースに対する結果セットのキャッシュを確認する

```sql
SELECT name, is_result_set_caching  
FROM sys.databases
```

### <a name="check-for-number-of-queries-with-result-set-cache-hit-and-cache-miss"></a>結果セットのキャッシュ ヒットとキャッシュ ミスと共にクエリの数を確認する

```sql
SELECT  
Queries=CacheHits+CacheMisses,
CacheHits,
CacheMisses,
CacheHitPct=CacheHits*1.0/(CacheHits+CacheMisses)
FROM  
(SELECT  
CacheHits=count(distinct case when s.command like '%DWResultCacheDb%' and
r.resource_class IS NULL and s.operation_type = 'ReturnOperation' and  
s.step_index = 0 then s.request_id else null end) ,
CacheMisses=count(distinct case when r.resource_class IS NOT NULL then  
s.request_id else null end)
     FROM sys.dm_pdw_request_steps s  
     JOIN sys.dm_pdw_exec_requests r  
     ON s.request_id = r.request_id) A
```

### <a name="check-for-result-set-cache-hit-or-cache-miss-for-a-query"></a>あるクエリに対する結果セットのキャッシュ ヒットまたはキャッシュ ミスを確認する

```sql
If
(SELECT step_index  
FROM sys.dm_pdw_request_steps  
WHERE request_id = 'QID58286'
      and operation_type = 'ReturnOperation'
      and command like '%DWResultCacheDb%') = 0
SELECT 1 as is_cache_hit  
ELSE
SELECT 0 as is_cache_hit
```

### <a name="check-for-all-queries-with-result-set-cache-hits"></a>結果セットにキャッシュ ヒットがあるクエリをすべて確認する

```sql
SELECT *  
FROM sys.dm_pdw_request_steps  
WHERE command like '%DWResultCacheDb%' and step_index = 0
```

## <a name="see-also"></a>参照

[SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)