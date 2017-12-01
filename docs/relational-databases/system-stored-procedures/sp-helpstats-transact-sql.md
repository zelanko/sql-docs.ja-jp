---
title: "sp_helpstats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpstats
- sp_helpstats_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpstats
ms.assetid: 00ab3cfd-2736-4fc0-b1b2-16dd49fb2fe5
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45d6df772da027568b1fbd7593e404f291246bb4
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpstats-transact-sql"></a>sp_helpstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定したテーブルの列およびインデックスに関する統計を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]統計に関する情報を取得するクエリ、 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)と[sys.stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)カタログ ビューです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpstats[ @objname = ] 'object_name'   
     [ , [ @results = ] 'value' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@objname=**] **'***object_name***'**  
 統計情報の提供元となるテーブルを指定します。 *object_name*は**nvarchar (520)** null にすることはできません。 1 つまたは 2 つの部分で構成される名前を指定できます。  
  
 [  **@results=**] **'***値***'**  
 提供する情報の範囲を指定します。 有効なエントリは**すべて**と**STATS**です。 **すべて**すべてのインデックスとも以外作例された統計がある列の統計情報を一覧表示**STATS**インデックスに関連付けられていない統計のみを表示します。 *値*は**nvarchar (5)**既定値は STATS です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の表では、結果セットの列について説明します。  
  
|列名|Description|  
|-----------------|-----------------|  
|**statistics_name**|統計の名前。 返します**sysname** null にすることはできません。|  
|**statistics_keys**|統計の基準となるキー。 返します**nvarchar (2078)** null にすることはできません。|  
  
## <a name="remarks"></a>解説  
 特定のインデックスまたは統計に関する詳細な統計情報を表示するには、DBCC SHOW_STATISTICS を使用します。 詳細については、次を参照してください。 [DBCC SHOW_STATISTICS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)と[sp_helpindex (& a) #40 です。TRANSACT-SQL と #41 です;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`sp_createstats` を実行し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内のすべてのユーザー テーブルを対象にして、条件を満たすすべての列に関する統計を 1 列ずつ作成します。 その後、`sp_helpstats`で作成された結果統計を検索するために実行されて、`Customer`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_createstats;  
GO  
EXEC sp_helpstats   
@objname = 'Sales.Customer',  
@results = 'ALL';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `statistics_name               statistics_keys`  
  
 `----------------------------  ----------------`  
  
 `_WA_Sys_00000003_22AA2996     AccountNumber`  
  
 `AK_Customer_AccountNumber     AccountNumber`  
  
 `AK_Customer_rowguid           rowguid`  
  
 `CustomerType                  CustomerType`  
  
 `IX_Customer_TerritoryID       TerritoryID`  
  
 `ModifiedDate                  ModifiedDate`  
  
 `PK_Customer_CustomerID        CustomerID`  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
