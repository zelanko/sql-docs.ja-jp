---
title: "DBCC SHOWCONTIG (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_SHOWCONTIG_TSQL
- DBCC SHOWCONTIG
- SHOWCONTIG
- SHOWCONTIG_TSQL
dev_langs: TSQL
helpviewer_keywords:
- displaying defragmentation information
- DBCC SHOWCONTIG statement
- defragmenting indexes
- leaf level defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
ms.assetid: 1df2123a-1197-4fff-91a3-25e3d8848aaa
caps.latest.revision: "78"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 85822d9351e0f0ce5a8c5a7542fbd7df57d13d74
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-showcontig-transact-sql"></a>DBCC SHOWCONTIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

指定されたテーブルまたはビューのデータとインデックスの断片化に関する情報を表示します。
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]使用して[sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)代わりにします。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC SHOWCONTIG   
[ (   
    { table_name | table_id | view_name | view_id }   
    [ , index_name | index_id ]   
) ]   
    [ WITH   
        {   
         [ , [ ALL_INDEXES ] ]   
         [ , [ TABLERESULTS ] ]   
         [ , [ FAST ] ]  
         [ , [ ALL_LEVELS ] ]   
         [ NO_INFOMSGS ]  
         }  
    ]  
```  
  
## <a name="arguments"></a>引数  
 *table_name* | *table_id* | *view_name* | *view_id*  
 断片化情報をチェックするテーブルまたはビューを指定します。 指定しない場合、現在のデータベース内のすべてのテーブルおよびインデックス付きビューがチェックされます。 テーブルを入手または ID を表示を使用して、 [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)関数。  
  
 *index_name* | *index_id*  
 断片化情報をチェックするインデックスを指定します。 インデックスを指定しない場合、ステートメントは指定されたテーブルまたはビューのベース インデックスを処理します。 インデックス ID を取得するを使用して、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。  
  
 のすべてのメンションを  
 DBCC ステートメントが返す情報の種類に関するオプションを指定します。  
  
 FAST  
 インデックスの高速スキャンを実行し、最小限の情報を出力するかどうかを指定します。 高速スキャンでは、インデックスのリーフ レベルまたはデータ レベルのページは読み込まれません。  
  
 ALL_INDEXES  
 特定のインデックスが指定されていても、指定されたテーブルおよびビューのすべてのインデックスに関する結果を表示します。  
  
 TABLERESULTS  
 追加情報を含めた結果を、行セットとして表示します。  
  
 ALL_LEVELS  
 旧バージョンとの互換性のためにだけ用意されています。 ALL_LEVELS が指定されている場合でも、インデックス リーフ レベルまたはテーブル データ レベルのみ処理されます。  
  
 NO_INFOMSGS  
 重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="result-sets"></a>結果セット  
次の表では、結果セットに表示される情報について説明します。
  
|統計情報|Description|  
|---|---|
|**スキャンされたページ数**|テーブルまたはインデックスのページ数です。|  
|**スキャンされたエクステント数**|テーブルまたはインデックスのエクステント数です。|  
|**エクステントの切り替え**|DBCC ステートメントがテーブルまたはインデックスのページを横断する間に 1 つのエクステントから別のエクステントに移動する回数です。|  
|**平均エクステントごとのページ**|ページ チェーンに存在するエクステント 1 つあたりのページ数です。|  
|**スキャン密度 [最善値: 実際のカウント]**|パーセンテージです。 比率は**最善値**に**実際のカウント**です。 すべて連続的にリンクされているときは、この値は 100 になります。100 未満の場合は、断片化が発生していることを示します。<br /><br /> **最善値**はすべて連続的にリンクされている場合に理想的なエクステント変更回数です。 **実際のカウント**エクステント変更の実際の数です。|  
|**論理スキャンの断片化**|インデックスのリーフ ページをスキャンするときに返される、順序が無効なページのパーセンテージです。 この数値はヒープとは関係ありません。 順序不定なページは、対象のインデックスに割り当てられている次の物理ページが不正なページを指す次ページ ページ*e*現在のリーフ ページのポインター。|  
|**エクステント スキャンの断片化**|インデックスのリーフ ページをスキャンするときの順序が無効なエクステントのパーセンテージです。 この数値はヒープとは関係ありません。 順序が無効なエクステントとは、インデックス上の現在のページを含むエクステントの物理的な位置が、インデックス上の前のページを含むエクステントの直後でない状態を指します。<br /><br /> 注: この番号はインデックスが複数のファイルにわたる場合に意味がなくなります。|  
|**平均1 ページあたりの空きバイト数**|スキャンしたページの平均の空きバイト数です。 数値が大きいほど、ページの密度が低くなります。 ランダムな挿入がそれほど行われないインデックスの場合は、小さい値の方が適しています。 この数値は行サイズの影響も受けます。行サイズが大きいと数値が大きくなります。|  
|**平均ページ密度 (全体)**|パーセンテージで表した平均ページ密度です。 この数値は行サイズを考慮しています。 このため、ページが満たされる程度に関してはより正確な指標になります。 パーセント値は、大きいほど適しています。|  
  
ときに*table_id*と高速は指定すると、DBCC SHOWCONTIG は次の列のみを含む結果セットを返します。
-   **スキャンされたページ数**  
-   **エクステントの切り替え**  
-   **スキャン密度 [最善値: 実際のカウント]**  
-   **エクステント スキャンの断片化**  
-   **論理スキャンの断片化**  
  
TABLERESULTS を指定した場合、DBCC SHOWCONTIG は次の列に加え、前の表で説明した 9 つの列も返します。
  
|統計情報|Description|  
|---|---|
|**[オブジェクト名]**|処理されるテーブルまたはビューの名前です。|  
|**ObjectId**|オブジェクト名の ID です。|  
|**IndexName**|処理されるインデックスの名前です。 ヒープの場合は NULL です。|  
|**IndexId**|インデックスの ID。 ヒープの場合は 0 です。|  
|**Level**|インデックスのレベルです。 レベル 0 は、インデックスのリーフ レベルまたはデータ レベルです。<br /><br /> ヒープの場合、レベルは 0 です。|  
|**[ページ]**|インデックスまたはヒープ全体のレベルを構成するページ数です。|  
|**行数**|指定したインデックスのレベルのデータまたはインデックス レコードの数です。 ヒープの場合は、ヒープ全体のデータ レコードの数です。<br /><br /> ヒープでは、この関数から返されるレコード数が、ヒープに対して SELECT COUNT(*) を実行したときに返される行数と一致しない場合があります。 これは、1 行に複数のレコードが含まれる場合があるためです。 たとえば、更新の状況によっては、更新操作の結果として転送元レコードと転送先レコードが 1 つのヒープ行に含まれることがあります。 また、大きな LOB 行のほとんどは、LOB_DATA ストレージ内で複数のレコードに分割されます。|  
|**MinimumRecordSize**|指定したインデックスのレベルまたはヒープ全体のレコードの最小サイズです。|  
|**MaximumRecordSize**|指定したインデックスのレベルまたはヒープ全体のレコードの最大サイズです。|  
|**AverageRecordSize**|指定したインデックスのレベルまたはヒープ全体の平均レコード サイズです。|  
|**ForwardedRecords**|指定したインデックスのレベルまたはヒープ全体の転送されたレコードの数です。|  
|**エクステント**|指定したインデックスのレベルまたはヒープ全体のエクステントの数です。|  
|**ExtentSwitches**|DBCC ステートメントがテーブルまたはインデックスのページを横断する間に 1 つのエクステントから別のエクステントに移動する回数です。|  
|**AverageFreeBytes**|スキャンしたページの平均の空きバイト数です。 数値が大きいほど、ページの密度が低くなります。 ランダムな挿入がそれほど行われないインデックスの場合は、小さい値の方が適しています。 この数値は行サイズの影響も受けます。行サイズが大きいと数値が大きくなります。|  
|**AveragePageDensity**|パーセンテージで表した平均ページ密度です。 この数値は行サイズを考慮しています。 このため、ページが満たされる程度に関してはより正確な指標になります。 パーセント値は、大きいほど適しています。|  
|**ScanDensity**|パーセンテージです。 比率は**BestCount**に**ActualCount**です。 すべて連続的にリンクされているときは、この値は 100 になります。100 未満の場合は、断片化が発生していることを示します。|  
|**BestCount**|すべて連続的にリンクされている場合の理想的なエクステント変更回数です。|  
|**ActualCount**|エクステント変更の実際の数です。|  
|**LogicalFragmentation**|インデックスのリーフ ページをスキャンするときに返される、順序が無効なページのパーセンテージです。 この数値はヒープとは関係ありません。 順序不定なページは、対象のインデックスに割り当てられている次の物理ページが不正なページを指す次ページ ページ*e*現在のリーフ ページのポインター。|  
|**ExtentFragmentation**|インデックスのリーフ ページをスキャンするときの順序が無効なエクステントのパーセンテージです。 この数値はヒープとは関係ありません。 順序が無効なエクステントとは、インデックス上の現在のページを含むエクステントの物理的な位置が、インデックス上の前のページを含むエクステントの直後でない状態を指します。<br /><br /> 注: この番号はインデックスが複数のファイルにわたる場合に意味がなくなります。|  
  
WITH TABLERESULTS および FAST を指定した場合の結果セットは WITH TABLERESULTS を指定した場合と同じです。ただし、次の列が NULL 値になります。

| 行数| Extents |
|---|---|
|**MinimumRecordSize**|**AverageFreeBytes**|  
|**MaximumRecordSize**|**AveragePageDensity**|  
|**AverageRecordSize**|**ExtentFragmentation**|  
|**ForwardedRecords**||  
  
## <a name="remarks"></a>解説  
DBCC SHOWCONTIG ステートメントが、指定のリーフ レベルでページ チェーンを移動するときにインデックス*index_id*を指定します。 だけの場合*table_id*が指定されている場合、または*index_id*が 0 の場合、指定したテーブルのデータ ページがスキャンされます。 この操作には、インテント共有 (IS) テーブル ロックのみが必要です。 この方法では、排他 (X) テーブル ロックが必要な場合を除き、すべての更新と挿入が実行できます。 これにより、実行の速度は速くなりますが、返される統計数に対する同時実行の数は削減されません。 ただし、このコマンドを断片化の測定のみに使用する場合は、最適なパフォーマンスを得るために WITH FAST オプションを指定することをお勧めします。 高速スキャンでは、インデックスのリーフ レベルまたはデータ レベルのページは読み込まれません。 WITH FAST オプションは、ヒープには適用されません。
  
## <a name="restrictions"></a>制限  
DBCC SHOWCONTIG にデータは表示されません**ntext**、**テキスト**、および**イメージ**データ型。 これは、テキストとイメージのデータが格納されているテキスト インデックスが存在しなくなったためです。
  
また、DBCC SHOWCONTIG でサポートされない新機能もあります。 例:
-   指定されたテーブルまたはインデックスがパーティション分割されている場合、DBCC SHOWCONTIG では指定されたテーブルまたはインデックスの最初のパーティションのみが表示されます。  
-   DBCC SHOWCONTIG は表示されません行オーバーフロー ストレージ情報とその他の新しい行外のデータ型など**nvarchar (max)**、 **varchar (max)**、 **varbinary (max)**、および**xml**です。  
-   空間インデックスは、DBCC SHOWCONTIG ではサポートされません。  
  
すべての新機能は完全にサポートによって、 [sys.dm_db_index_physical_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)動的管理ビュー。
  
## <a name="table-fragmentation"></a>テーブルの断片化  
DBCC SHOWCONTIG は、テーブルに著しい断片化が生じているかどうかを調べます。 テーブルの断片化は、テーブルに対するデータの変更処理 (INSERT、UPDATE、DELETE ステートメント) によって発生します。 このような変更処理は、テーブルのすべての行にわたって均等に分散するわけではないので、時間の経過と共に、各ページの充填率に差が生じることがあります。 そのため、テーブルの一部または全体をスキャンするクエリでは、このようなテーブルの断片化によって、余分なページ読み込みが必要になり、 データの並列スキャンの妨げになります。
  
インデックスが著しく断片化している場合、断片化を減らす方法は次のとおりです。
-   クラスター化インデックスを削除し、再作成します。  
     クラスター化インデックスを再作成すると、データが再構成され、データ ページがデータで満たされます。 ページのゆとりのレベルは、CREATE INDEX の FILLFACTOR オプションを使用して構成できます。 この方法の短所は、削除と再作成のサイクルの間インデックスがオフラインになることと、その操作がアトミックであることです。 インデックスの作成が中断されると、インデックスは再作成されません。  
-   インデックスのリーフ レベルのページを論理順序の順に並べ替えます。  
     ALTER INDEX...REORGANIZE を使用してインデックスのリーフ レベル ページを論理順序の順に並べ替えます。 この操作はオンライン操作であるため、ステートメントを実行しているときにインデックスが使用できます。 この操作は、完了済みの作業を失わずに中断することもできます。 この方法の短所は、クラスター化インデックスの削除と再作成の操作よりも、データの再構成において劣ることです。  
-   インデックスを再構築します。  
     REBUILD を設定した ALTER INDEX を使用して、インデックスを再構築します。 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)」を参照してください。  
  
**Avg.1 ページあたりの空きバイト数**と**avg.ページ密度 (全体)**結果セット内の統計がインデックス ページの充填率を示します。 **Avg.1 ページあたりの空きバイト数**数が不足している必要があります、 **avg.ページ密度 (全体)**数が高のランダムな挿入はありませんインデックスにする必要があります。 インデックスを削除し、FILLFACTOR オプションを指定して再作成を行うと、これらの統計が改善されます。 また、REORGANIZE と併用する ALTER INDEX コマンドは、インデックスの FILLFACTOR を考慮しながらインデックスを最適化するので、これらの統計が改善されます。
  
> [!NOTE]  
>  ランダム挿入が多く、ページの密度が高いインデックスは、ページ分割の数が増えます。 断片化が大きくなります。  
  
インデックスの断片化レベルは、次の方法で確認できます。
-   値を比較して**エクステントの切り替え回数**と**スキャンされたエクステント数**です。  
     値**エクステントの切り替え回数**のものに限り近くする必要があります**スキャンされたエクステント数**です。 この比率の計算は、**スキャン密度**値。 この値はできるだけ高くし、インデックスの断片化を削減することで改善できます。  
  
    > [!NOTE]  
    >  この方法は、インデックスが複数のファイルにわたっている場合は使用できません。  
  
-   理解することにより**論理スキャンの断片化**と**エクステント スキャンの断片化**値。  
     **論理スキャンの断片化**と程度は低くなります**エクステント スキャンの断片化**値は、テーブルの断片化レベルの最善の指標です。 0 ～ 10% は許容範囲ですが、この 2 つの値はできるだけ 0 に近い値にする必要があります。  
  
    > [!NOTE]  
    >  **エクステント スキャンの断片化**値は、インデックスが複数のファイルにわたる場合に大きくなります。 これらの値を小さくするには、インデックスの断片化を削減する必要があります。  
  
## <a name="permissions"></a>Permissions  
ユーザーが、テーブルを所有またはのメンバーである必要があります、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、または**db_ddladmin**固定データベース ロール。
  
## <a name="examples"></a>使用例  
### <a name="a-displaying-fragmentation-information-for-a-table"></a>A. テーブルの断片化情報を表示する  
次の例では、`Employee` テーブルの断片化情報を表示します。
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG ('HumanResources.Employee');  
GO  
```  
  
### <a name="b-using-objectid-to-obtain-the-table-id-and-sysindexes-to-obtain-the-index-id"></a>B. OBJECT_ID を使用してテーブル ID を取得し、sysindexes を使用してインデックス ID を取得する  
次の例で`OBJECT_ID`と`sys.indexes`カタログ ビューをテーブル ID を取得し、インデックスの ID、`AK_Product_Name`のインデックス、`Production.Product`テーブルに、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @id int, @indid int  
SET @id = OBJECT_ID('Production.Product')  
SELECT @indid = index_id   
FROM sys.indexes  
WHERE object_id = @id   
   AND name = 'AK_Product_Name'  
DBCC SHOWCONTIG (@id, @indid);  
GO  
```  
  
### <a name="c-displaying-an-abbreviated-result-set-for-a-table"></a>C. テーブルの簡略な結果セットを表示する  
次の例は、簡略な結果のセットを返します、`Product`テーブルに、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG ('Production.Product', 1) WITH FAST;  
GO  
```  
  
### <a name="d-displaying-the-full-result-set-for-every-index-on-every-table-in-a-database"></a>D. データベースに含まれる全テーブルの全インデックスの完全な結果セットを表示する  
次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに含まれる全テーブルの全インデックスの完全な結果セットを返します。
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG WITH TABLERESULTS, ALL_INDEXES;  
GO  
```  
  
### <a name="e-using-dbcc-showcontig-and-dbcc-indexdefrag-to-defragment-the-indexes-in-a-database"></a>E. DBCC SHOWCONTIG と DBCC INDEXDEFRAG を使用してデータベース内のインデックスの断片化を解消する  
次の例では、宣言されたしきい値を超えて断片化しているデータベースのすべてのインデックスの断片化を解消する簡単な方法を示します。
  
```sql
/*Perform a 'USE <database name>' to select the database in which to run the script.*/  
-- Declare variables  
SET NOCOUNT ON;  
DECLARE @tablename varchar(255);  
DECLARE @execstr   varchar(400);  
DECLARE @objectid  int;  
DECLARE @indexid   int;  
DECLARE @frag      decimal;  
DECLARE @maxfrag   decimal;  
  
-- Decide on the maximum fragmentation to allow for.  
SELECT @maxfrag = 30.0;  
  
-- Declare a cursor.  
DECLARE tables CURSOR FOR  
   SELECT TABLE_SCHEMA + '.' + TABLE_NAME  
   FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_TYPE = 'BASE TABLE';  
  
-- Create the table.  
CREATE TABLE #fraglist (  
   ObjectName char(255),  
   ObjectId int,  
   IndexName char(255),  
   IndexId int,  
   Lvl int,  
   CountPages int,  
   CountRows int,  
   MinRecSize int,  
   MaxRecSize int,  
   AvgRecSize int,  
   ForRecCount int,  
   Extents int,  
   ExtentSwitches int,  
   AvgFreeBytes int,  
   AvgPageDensity int,  
   ScanDensity decimal,  
   BestCount int,  
   ActualCount int,  
   LogicalFrag decimal,  
   ExtentFrag decimal);  
  
-- Open the cursor.  
OPEN tables;  
  
-- Loop through all the tables in the database.  
FETCH NEXT  
   FROM tables  
   INTO @tablename;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
-- Do the showcontig of all indexes of the table  
   INSERT INTO #fraglist   
   EXEC ('DBCC SHOWCONTIG (''' + @tablename + ''')   
      WITH FAST, TABLERESULTS, ALL_INDEXES, NO_INFOMSGS');  
   FETCH NEXT  
      FROM tables  
      INTO @tablename;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE tables;  
DEALLOCATE tables;  
  
-- Declare the cursor for the list of indexes to be defragged.  
DECLARE indexes CURSOR FOR  
   SELECT ObjectName, ObjectId, IndexId, LogicalFrag  
   FROM #fraglist  
   WHERE LogicalFrag >= @maxfrag  
      AND INDEXPROPERTY (ObjectId, IndexName, 'IndexDepth') > 0;  
  
-- Open the cursor.  
OPEN indexes;  
  
-- Loop through the indexes.  
FETCH NEXT  
   FROM indexes  
   INTO @tablename, @objectid, @indexid, @frag;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   PRINT 'Executing DBCC INDEXDEFRAG (0, ' + RTRIM(@tablename) + ',  
      ' + RTRIM(@indexid) + ') - fragmentation currently '  
       + RTRIM(CONVERT(varchar(15),@frag)) + '%';  
   SELECT @execstr = 'DBCC INDEXDEFRAG (0, ' + RTRIM(@objectid) + ',  
       ' + RTRIM(@indexid) + ')';  
   EXEC (@execstr);  
  
   FETCH NEXT  
      FROM indexes  
      INTO @tablename, @objectid, @indexid, @frag;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE indexes;  
DEALLOCATE indexes;  
  
-- Delete the temporary table.  
DROP TABLE #fraglist;  
GO  
```  
  
## <a name="see-also"></a>参照  
[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)  
[sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)
  
  

