---
title: cdc.fn_cdc_get_net_changes_&lt;capture_instance&gt; (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_net_changes_<capture_instance>
- change data capture [SQL Server], querying metadata
- cdc.fn_cdc_get_net_changes_<capture_instance>
ms.assetid: 43ab0d1b-ead4-471c-85f3-f6c4b9372aab
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 853392a1a2db64c832c93d633def5dff30acceb6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="cdcfncdcgetnetchangesltcaptureinstancegt-transact-sql"></a>cdc.fn_cdc_get_net_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したログ シーケンス番号 (LSN) 範囲内で変更されたソース行ごとに 1 つの差分変更行を返します。  
  
 **待機の特定の LSN は何ですか。** すべてのレコード、 [SQL Server トランザクション ログ](../logs/the-transaction-log-sql-server.md)はログ シーケンス番号 (LSN) によって一意に識別します。 Lsn は、LSN2 によって参照されるログ レコードで変更が発生した場合は、LSN2 が LSN1 より大きいになるように順序付けられている**後**ログ レコードの LSN によって変更します。  
  
 重要なイベントが発生したログ レコードの LSN は、正しい復元シーケンスを構築するために役立ちます。 等値演算子および非等値の比較できます Lsn の順序は、ため (つまり、 \<、>、=、 \<=、> =)。 このような比較は、復元シーケンスを構築するときに役立ちます。  
  
 ソース行では、LSN 範囲の中に複数の変更がある、次に示す、列挙関数によって、行の最終的な内容を反映する 1 つの行が返されます。 たとえば、トランザクションがソース テーブルに行を挿入すると、LSN 範囲内の後続のトランザクションがその行に 1 つまたは複数の列を更新、関数だけを返す**1**行は、更新された列の値が含まれています。  
  
 この列挙関数は、ソース テーブルに対して変更データ キャプチャを有効にし、かつ、差分追跡を指定した場合に作成されます。 差分追跡を有効にするには、ソース テーブルに主キーまたは一意のインデックスが必要です。 関数の名前は派生し、形式 cdc.fn_cdc_get_net_changes_*capture_instance*ここで、 *capture_instance*は値をソース テーブルが、キャプチャ インスタンスの指定変更データ キャプチャを有効にします。 詳細については、次を参照してください。 [sys.sp_cdc_enable_table &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
cdc.fn_cdc_get_net_changes_capture_instance ( from_lsn , to_lsn , '<row_filter_option>' )  
  
<row_filter_option> ::=  
{ all  
 | all with mask  
 | all with merge  
}  
```  
  
## <a name="arguments"></a>引数  
 *from_lsn*  
 結果セットに含める LSN 範囲の下端を表す LSN を指定します。 *from_lsn* is **binary(10)**.  
  
 内の行のみ、 [cdc。 &#91; capture_instance &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) _ _ $start_lsn に以上の値を持つテーブルを変更する*from_lsn*結果セットに含まれます。  
  
 *to_lsn*  
 結果セットに含める LSN 範囲の上端を表す LSN を指定します。 *to_lsn*は**binary (10)**です。  
  
 内の行のみ、 [cdc &#91; capture_instance &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) _ _ $start_lsn 以上の値を持つテーブルを変更*from_lsn*以上*to_lsn*は。結果セットに含まれています。  
  
 *< row_filter_option >* :: = {すべて | マスクを持つすべて | 結合をすべて含む}  
 結果セットに返される行と同様に、メタデータ列の内容を制御するオプションです。 次のいずれかのオプションを指定できます。  
  
 all  
 行およびメタデータ列 _ _ $start_lsn の行を適用するために必要な操作の最終的な変更の LSN を返しますと\_ \_$operation です。 列\_ \_$update_mask は常に NULL です。  
  
 all with mask  
 行およびメタデータ列 _ _ $start_lsn の行を適用するために必要な操作の最終的な変更の LSN を返しますと\_ \_$operation です。 さらに、更新操作を返す場合 (\_\_$operation = 4) で返される値で更新プログラムで変更のキャプチャ対象列がマークされている\_ \_$update_mask します。  
  
 all with merge  
 行に対する最終的な変更の LSN が、メタデータ列 __$start_lsn に返されます。 列\_ \_$operation には、2 つの値のいずれかになります。 削除と変更を適用するために必要な操作が挿入または更新プログラムのいずれかであることを示す 5 の場合は 1 です。 列\_ \_$update_mask は常に NULL です。  
  
 特定の変更に必要な操作を厳密に特定するロジックではクエリが複雑になってしまいます。そのため、このオプションでは、変更データの適用に必要な操作が、挿入と更新のいずれかであることがわかればよく、両者を明確に区別する必要がない場合に、より高いパフォーマンスでクエリを実行できるように設計されています。 このオプションは、マージ操作が、直接などに使用できるターゲット環境で最も魅力的な[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]環境。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|__$start_lsn|**binary(10)**|変更のコミット トランザクションに関連付けられた LSN。<br /><br /> 同じトランザクションでコミットされたすべての変更は、同じコミット LSN を共有します。 たとえば、ソース テーブルの更新操作は、2 つの行に 2 つの列を変更する場合、変更テーブルの同じ _ _ $start_lsnvalue 4 つの行が含まれます。|  
|__$operation|**int**|変更データの行をターゲット データ ソースに適用するために必要となった DML (データ操作言語) 操作を識別します。<br /><br /> row_filter_option パラメーターの値が all または all with mask である場合、この列の値には、次のいずれかの値を指定できます。<br /><br /> 1 = 削除<br /><br /> 2 = 挿入<br /><br /> 4 = 更新<br /><br /> row_filter_option パラメーターの値が all with merge である場合、この列の値には、次のいずれかの値を指定できます。<br /><br /> 1 = 削除|  
|__$update_mask|**varbinary (128)**|キャプチャ インスタンスに対して指定された各キャプチャ対象列に対応するビットを持ったビット マスク。 __$operation が 1 または 2 の場合、定義されているすべてのビットが 1 に設定されます。 ときに\_ \_$operation = 3 または 4、変更された列に対応するビットだけが 1 に設定されます。|  
|*\< キャプチャ対象のソース テーブルの列 >*|各種|この関数によって返されるその他の列は、ソース テーブルの列のうち、キャプチャ インスタンスの作成時にキャプチャ対象として指定された列です。 キャプチャ対象列リストで列が指定されなかった場合、ソース テーブルのすべての列が返されます。|  
  
## <a name="permissions"></a>権限  
 固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーシップが必要です。 それ以外のすべてのユーザーについては、ソース テーブルのすべてのキャプチャ対象列に対する SELECT 権限が必要です。さらに、キャプチャ インスタンスのゲーティング ロールが定義されている場合は、そのデータベース ロールのメンバーシップが必要です。 呼び出し元にソース データを表示する権限がなかった場合、エラー 208 (無効なオブジェクト名) が返されます。  
  
## <a name="remarks"></a>解説  
 指定した LSN 範囲が、キャプチャ インスタンスの変更追跡時間外に該当した場合、エラー 208 (無効なオブジェクト名) が返されます。  
  
## <a name="examples"></a>使用例  
 次の例は、関数を使用して`cdc.fn_cdc_get_net_changes_HR_Department`net に、ソース テーブルに加えられた変更を報告する`HumanResources.Department`特定の時間間隔中にします。  
  
 最初に、`GETDATE`関数を使用して時間間隔の開始をマークします。 ソース テーブルに対して複数の DML ステートメントを適用した後、再び `GETDATE` 関数を呼び出して期間の終わりを指定します。 関数は、 [sys.fn_cdc_map_time_to_lsn](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)時間間隔を変更データ キャプチャのクエリ範囲の LSN 値で範囲指定にマップを使用して、します。 最後に、`cdc.fn_cdc_get_net_changes_HR_Department` 関数を呼び出して、該当期間中に行われたソース テーブルへの差分変更を取得します。 挿入後に削除された行については、関数から返される結果セットに含まれません。 たとえ行を追加しても、同じ期間内に削除されれば、その期間におけるソース テーブルへの差分変更とはならないためです。 この例を実行する前に例 B を初めて実行する必要があります[sys.sp_cdc_enable_table &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @begin_time datetime, @end_time datetime, @from_lsn binary(10), @to_lsn binary(10);  
-- Obtain the beginning of the time interval.  
SET @begin_time = GETDATE() -1;  
-- DML statements to produce changes in the HumanResources.Department table.  
INSERT INTO HumanResources.Department (Name, GroupName)  
VALUES (N'MyDept', N'MyNewGroup');  
  
UPDATE HumanResources.Department  
SET GroupName = N'Resource Control'  
WHERE GroupName = N'Inventory Management';  
  
DELETE FROM HumanResources.Department  
WHERE Name = N'MyDept';  
  
-- Obtain the end of the time interval.  
SET @end_time = GETDATE();  
-- Map the time interval to a change data capture query range.  
SET @from_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than or equal', @begin_time);  
SET @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);  
  
-- Return the net changes occurring within the query window.  
SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@from_lsn, @to_lsn, 'all');  
```  
  
## <a name="see-also"></a>参照  
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
