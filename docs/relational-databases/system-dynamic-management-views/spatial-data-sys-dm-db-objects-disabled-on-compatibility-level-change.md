---
title: sys.dm_db_objects_disabled_on_compatibility_level_change (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_objects_disabled_on_compatibility_level_change
- dm_db_objects_disabled_on_compatibility_level_change_TSQL
- sys.dm_db_objects_disabled_on_compatibility_level_change
- sys.dm_db_objects_disabled_on_compatibility_level_change_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_objects_disabled_on_compatibility_level_change catalog view
ms.assetid: a5d70064-0330-48b9-b853-01eba50755d0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f52daf2257ac6a2d8ea34d61ed2dd869b0363bce
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spatial-data---sysdmdbobjectsdisabledoncompatibilitylevelchange"></a>空間データは - sys.dm_db_objects_disabled_on_compatibility_level_change
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  インデックスとの互換性レベルを変更した結果として無効になる制約一覧[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 保存される計算列が含まれているインデックスまたは制約があり、計算式に空間 UDT が使用されている場合に、互換性レベルをアップグレードまたは変更すると、このインデックスまたは制約は無効になります。 この動的管理関数は、互換性レベルの変更の影響を調べる際に使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
sys.dm_db_objects_disabled_on_compatibility_level_change ( compatibility_level )   
```  
  
##  <a name="Arguments"></a> 引数  
 *compatibility_level*  
 **int**設定を計画している、互換性レベルを識別します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**class**|**int**|1 = 制約<br /><br /> 7 = インデックスとヒープ|  
|**class_desc**|**nvarchar(60)**|制約の場合は OBJECT または COLUMN<br /><br /> インデックスとヒープの場合は INDEX|  
|**major_id**|**int**|制約の OBJECT ID <br /><br /> インデックスとヒープが含まれたテーブルの OBJECT ID|  
|**minor_id**|**int**|制約の場合は NULL<br /><br /> インデックスとヒープの場合は Index_id|  
|**dependency**|**nvarchar(60)**|制約またはインデックスを無効にするような依存関係の説明。 アップグレード中に発生した警告にも同じ値が使用されます。 次の例に示します。<br /><br /> 組み込みの場合は "space"<br /><br /> システム UDT の場合は "geometry"<br /><br /> システム UDT のメソッドの場合は "geography::Parse"|  
  
## <a name="general-remarks"></a>全般的な解説  
 互換性レベルを変更すると、一部の組み込み関数を使用している保存される計算列が無効になります。 データベースをアップグレードすると、Geometry メソッドまたは Geography メソッドを使用している保存される計算列も無効になります。  
  
### <a name="which-functions-cause-persisted-computed-columns-to-be-disabled"></a>保存される計算列を無効にする関数   
 保存される計算列の式で、次の関数を使用している場合、互換性レベルが 80 からを 90 に変更されたときに無効にするには、その列を参照するインデックスと制約をが。  
  
-   **IsNumeric**  
  
 保存される計算列の式で次の関数が使用されている場合、互換性レベルが 100 から 110 以上に変更されると、これらの列を参照するインデックスと制約が無効になります。  
  
-   **Soundex**  
  
-   **Geography:: GeomFromGML**  
  
-   **Geography:: STGeomFromText**  
  
-   **Geography:: STLineFromText**  
  
-   **Geography:: STPolyFromText**  
  
-   **Geography:: STMPointFromText**  
  
-   **Geography:: STMLineFromText**  
  
-   **Geography:: STMPolyFromText**  
  
-   **Geography:: STGeomCollFromText**  
  
-   **Geography:: STGeomFromWKB**  
  
-   **Geography:: STLineFromWKB**  
  
-   **Geography:: STPolyFromWKB**  
  
-   **Geography:: STMPointFromWKB**  
  
-   **Geography:: STMLineFromWKB**  
  
-   **Geography:: STMPolyFromWKB**  
  
-   **Geography:: STUnion**  
  
-   **Geography:: STIntersection**  
  
-   **Geography:: STDifference**  
  
-   **Geography:: STSymDifference**  
  
-   **Geography:: STBuffer**  
  
-   **Geography:: BufferWithTolerance**  
  
-   **Geography:: 解析**  
  
-   **Geography:: を減らす**  
  
### <a name="behavior-of-the-disabled-objects"></a>無効になったオブジェクトの動作  
 **インデックス**  
  
 クラスター化インデックスが無効になっているか、非クラスター化インデックスが強制された場合、次のエラーが発生する場合:"、クエリ プロセッサは、プランを作成することは、インデックス ' % です。\*'%.*ls' のテーブルまたはビューで ' % です。\*'%.*ls' が無効です"。 これらのオブジェクトを再度有効に、インデックスを再構築のアップグレード後に呼び出すことによって**ALTER INDEX ON しています.再構築**です。  
  
 **ヒープ**  
  
 無効になったヒープが含まれているテーブルを使用すると、次のエラーが発生します。 呼び出してアップグレード後に再構築すると、これらのオブジェクトを再度有効にするには、**インデックスのすべての変更.再構築**です。  
  
```  
// ErrorNumber: 8674  
// ErrorSeverity: EX_USER  
// ErrorFormat: The query processor is unable to produce a plan because the table or view '%.*ls' is disabled.  
// ErrorCause: The table has a disabled heap.   
// ErrorCorrectiveAction: Rebuild the disabled heap to enable it.   
// ErrorInserts: table or view name   
// ErrorOwner: mtintor   
// ErrorFirstProduct: SQL11  
```  
  
 オンライン操作中に、ヒープを再構築しようとすると、エラーが発生します。  
  
 **Check 制約と外部キー**  
  
 無効になった CHECK 制約と外部キーを使用しても、エラーは発生しません。 ただし、行が変更されても、制約は適用されません。 これらのオブジェクトを再度有効にするを呼び出すことによってアップグレードした後、制約をチェック**ALTER TABLE.CHECK 制約**です。  
  
 **保存される計算列**  
  
 1 つの列を無効にすることはできないので、クラスター化インデックスまたはヒープを無効にすると、テーブル全体が無効になります。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 VIEW DATABASE STATE 権限が必要です。  
  
## <a name="example"></a>例  
 次の例のクエリを示しています**sys.dm_db_objects_disabled_on_compatibility_level_change**を互換性レベルを 120 に変更することによって影響を受けるオブジェクトを検索します。  
  
```sql  
SELECT * FROM sys.dm_db_objects_disabled_on_compatibility_level_change(120);  
GO  
  
```  
  
  
