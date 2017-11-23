---
title: "sp_autostats (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_autostats_TSQL
- sp_autostats
dev_langs: TSQL
helpviewer_keywords: sp_autostats
ms.assetid: d1df8c15-ee73-49eb-9d13-6e98943c3e38
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a88a5d19b80ccb69272fab4c2b3e4ba7f87894a7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spautostats-transact-sql"></a>sp_autostats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  インデックス、統計オブジェクト、テーブル、またはインデックス付きビューの自動統計更新オプション (AUTO_UPDATE_STATISTICS) を表示または変更します。  
  
 AUTO_UPDATE_STATISTICS オプションの詳細については、次を参照してください。 [ALTER DATABASE SET Options &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-set-options.md)と[統計](../../relational-databases/statistics/statistics.md)です。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_autostats [ @tblname = ] 'table_or_indexed_view_name'   
    [ , [ @flagc = ] 'stats_value' ]   
    [ , [ @indname = ] 'statistics_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@tblname=** ] **'***table_or_indexed_view_name***'**  
 AUTO_UPDATE_STATISTICS オプションを表示するテーブルまたはインデックス付きビューの名前を指定します。 *table_or_indexed_view_name*は**nvarchar (776)**、既定値はありません。  
  
 [  **@flagc=** ] **'***stats_value***'**  
 AUTO_UPDATE_STATISTICS オプションを次のいずれかの値に更新します。  
  
 **ON** = ON  
  
 **OFF** = OFF  
  
 ときに*stats_flag*が指定されていない AUTO_UPDATE_STATISTICS の現在の設定を表示します。 *stats_value*は**varchar (10)**、既定値は NULL です。  
  
 [  **@indname=** ] **'***statistics_name***'**  
 AUTO_UPDATE_STATISTICS オプションを表示または更新する統計の名前を指定します。 インデックスの統計を表示する場合は、インデックスの名前を使用できます。インデックスの名前は、対応する統計オブジェクトの名前と同じです。  
  
 *statistics_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 場合*stats_flag*が指定されている**sp_autostats**が取得されたが結果セットを返さないアクションを報告します。  
  
 場合*stats_flag*が指定されていない**sp_autostats**次の結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**Index Name**|**varchar(60)**|インデックスまたは統計の名前です。|  
|**AUTOSTATS**|**varchar (3)**|AUTO_UPDATE_STATISTICS オプションの現在の値。|  
|**最終更新日**|**datetime**|統計が最後に更新された日付。|  
  
 結果セットのテーブルまたはインデックス付きビューにインデックスを 1 列の統計、AUTO_CREATE_STATISTICS オプションを使用して生成用に作成された統計情報が含まれていますで作成された統計情報、 [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)ステートメントです。  
  
## <a name="remarks"></a>解説  
 指定したインデックスが無効な場合、または指定したテーブルに無効なクラスター化インデックスがある場合は、エラー メッセージが表示されます。  
  
 AUTO_UPDATE_STATISTICS はメモリ最適化テーブルでは常に OFF です。  
  
## <a name="permissions"></a>Permissions  
 オプションを AUTO_UPDATE_STATISTICS を変更するにはメンバーシップ n が必要です、 **db_owner**の固定データベース ロール、または ALTER 権限*table_name*です。オプションを AUTO_UPDATE_STATISTICS を表示するにはメンバーシップが必要です、**パブリック**ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-display-the-status-of-all-statistics-on-a-table"></a>A. テーブルのすべての統計の状態を表示する  
 次のすべての統計情報のステータスを表示する、`Product`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product';  
GO  
```  
  
### <a name="b-enable-autoupdatestatistics-for-all-statistics-on-a-table"></a>B. テーブルのすべての統計の AUTO_UPDATE_STATISTICS を有効にする  
 次の例では、`Product` テーブルのすべての統計の AUTO_UPDATE_STATISTICS オプションを有効にします。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product', 'ON';  
GO  
```  
  
### <a name="c-disable-autoupdatestatistics-for-a-specific-index"></a>C. 特定のインデックスの AUTO_UPDATE_STATISTICS を無効にする  
 次の例では、AUTO_UPDATE_STATISTICS オプションを`AK_Product_Name`のインデックス、`Product`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product', 'OFF', AK_Product_Name;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [統計情報](../../relational-databases/statistics/statistics.md)   
 [ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_createstats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
