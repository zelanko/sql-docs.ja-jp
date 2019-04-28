---
title: sys.dm_db_objects_disabled_on_compatibility_level_change (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fece91698147ef11496855985f27ea81f84f62a5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62669450"
---
# <a name="spatial-data---sysdmdbobjectsdisabledoncompatibilitylevelchange"></a>空間データの sys.dm_db_objects_disabled_on_compatibility_level_change
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  インデックスとの互換性レベルを変更した結果として無効になる制約一覧[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 アップグレードするか、互換性レベルを変更した後は、式を持つ空間 Udt を使用して、保存される計算列を格納するインデックスと制約を無効化されます。 この動的管理関数を使用して、互換性レベルでの変更の影響を判断します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
sys.dm_db_objects_disabled_on_compatibility_level_change ( compatibility_level )   
```  
  
##  <a name="Arguments"></a> 引数  
 *compatibility_level*  
 **int**を設定する互換性レベルを識別します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**class**|**int**|1 = 制約<br /><br /> 7 = インデックスとヒープ|  
|**class_desc**|**nvarchar(60)**|制約の場合は OBJECT または COLUMN<br /><br /> インデックスのインデックスとヒープ|  
|**major_id**|**int**|制約の OBJECT ID <br /><br /> インデックスとヒープを含んでいるテーブルのオブジェクト ID|  
|**minor_id**|**int**|制約の場合は NULL<br /><br /> インデックスとヒープの場合は Index_id|  
|**dependency**|**nvarchar(60)**|制約またはインデックスを無効にする原因となっている依存関係の説明です。 同じの値は、アップグレード中に発生した警告にも使用されます。 次の例に示します。<br /><br /> 組み込みの「領域」<br /><br /> システム UDT の場合は "geometry"<br /><br /> システム UDT のメソッドの場合は "geography::Parse"|  
  
## <a name="general-remarks"></a>全般的な解説  
 互換性レベルを変更すると、一部の組み込み関数を使用している保存される計算列が無効になります。 データベースをアップグレードすると、Geometry メソッドまたは Geography メソッドを使用している保存される計算列も無効になります。  
  
### <a name="which-functions-cause-persisted-computed-columns-to-be-disabled"></a>どの関数保存される計算列を無効にするか。  
 保存される計算列の式で、次の関数を使用している場合、互換性レベルが 80 からを 90 に変更されたときに無効にする列を参照するインデックスと制約をが。  
  
-   **IsNumeric**  
  
 保存される計算列の式で次の関数が使用されている場合、互換性レベルが 100 から 110 以上に変更されると、これらの列を参照するインデックスと制約が無効になります。  
  
-   **Soundex**  
  
-   **Geography:。GeomFromGML**  
  
-   **Geography:。STGeomFromText**  
  
-   **Geography:。STLineFromText**  
  
-   **Geography:。STPolyFromText**  
  
-   **Geography:。STMPointFromText**  
  
-   **Geography:。STMLineFromText**  
  
-   **Geography:。STMPolyFromText**  
  
-   **Geography:。STGeomCollFromText**  
  
-   **Geography:。STGeomFromWKB**  
  
-   **Geography:。STLineFromWKB**  
  
-   **Geography:。STPolyFromWKB**  
  
-   **Geography:。STMPointFromWKB**  
  
-   **Geography:。STMLineFromWKB**  
  
-   **Geography:。STMPolyFromWKB**  
  
-   **Geography:。STUnion**  
  
-   **Geography:。STIntersection**  
  
-   **Geography:。STDifference**  
  
-   **Geography:。STSymDifference**  
  
-   **Geography:。STBuffer**  
  
-   **Geography:。BufferWithTolerance**  
  
-   **Geography:。解析**  
  
-   **Geography:。削減**  
  
### <a name="behavior-of-the-disabled-objects"></a>無効になったオブジェクトの動作  
 **[インデックス]**  
  
 クラスター化インデックスが無効になっている場合、または非クラスター化インデックスが強制された場合は、次のエラーが発生します。"、クエリ プロセッサはプランを作成することは、インデックス ' % です。\*ls' テーブルまたはビュー ' % です。\*ls' が無効になっています"。 これらのオブジェクトを再度有効にするには、呼び出すことによってアップグレード後に、インデックスをリビルドします**ALTER INDEX ON しています.。REBUILD** を使用して変更するときに選択できます。  
  
 **ヒープ**  
  
 無効になったヒープが含まれているテーブルを使用すると、次のエラーが発生します。 呼び出してアップグレード後に再構築すると、これらのオブジェクトを再度有効にするには、**インデックスのすべての変更.REBUILD** を使用して変更するときに選択できます。  
  
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
  
 Check 制約を無効になっていると、外部キーにはエラーは発生しません。 ただし、行が変更されても、制約は適用されません。 これらのオブジェクトを再度有効にするには、呼び出すことによってアップグレードした後、制約を確認します**ALTER TABLE.。CHECK 制約**します。  
  
 **保存される計算列**  
  
 1 つの列を無効にすることはできないので、クラスター化インデックスまたはヒープを無効にすると、テーブル全体が無効になります。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 VIEW DATABASE STATE 権限が必要です。  
  
## <a name="example"></a>例  
 次の例ではクエリを示します**sys.dm_db_objects_disabled_on_compatibility_level_change**互換性レベル 120 に変更によって影響を受けるオブジェクトを検索します。  
  
```sql  
SELECT * FROM sys.dm_db_objects_disabled_on_compatibility_level_change(120);  
GO  
  
```  
  
  
