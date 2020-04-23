---
title: dm_pdw_exec_requests (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4f4ebcbf84da7d899b4d4cbd861cfb2ae3f75863
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087562"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>dm_pdw_exec_requests (トランザクション-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  で現在または最近アクティブなすべての要求に関する[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]情報を保持します。 要求/クエリごとに 1 行のリストを表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|このビューのキー。 要求に関連付けられた一意の数値 ID。|システム内のすべての要求で一意です。|  
|session_id|**nvarchar(32)**|このクエリが実行されたセッションに関連付けられた一意の数値 ID。 [「トランザクション SQL&#41;&#40;sys.dm_pdw_exec_sessions」](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)を参照してください。||  
|status|**nvarchar(32)**|要求の現在の状態です。|「実行中」「中断」「完了」「キャンセル」「失敗」。|  
|submit_time|**datetime**|要求が実行のために送信された時刻。|現在の日時とstart_timeより小さいか等しい有効な**日時**。|  
|start_time|**datetime**|要求の実行が開始された時刻。|キューに入っている要求の場合は NULL。それ以外の場合は、有効な**日時**が現在時刻より小さいか、または等しい。|  
|end_compile_time|**datetime**|エンジンが要求のコンパイルを完了した時刻。|まだコンパイルされていない要求の場合は NULL。それ以外の場合は、有効な**日時**がstart_time未満、現在の時刻以下になります。|
|end_time|**datetime**|要求実行が完了したか、失敗したか、または取り消された時刻。|キューに入れまたはアクティブな要求の場合は null。それ以外の場合は、有効な**日時**を現在の時刻より小さくするか、または等しい。|  
|total_elapsed_time|**int**|要求が開始されてからの実行時間 (ミリ秒単位)。|0 とstart_timeとend_timeの差の間。</br></br> 整数の最大値を超total_elapsed_time場合、total_elapsed_timeは引き続き最大値になります。 この条件により、「最大値を超えました」という警告が生成されます。</br></br> ミリ秒単位の最大値は、24.8 日と同じです。|  
|label|**nvarchar(255)**|SELECT クエリ ステートメントに関連付けられているオプションのラベル文字列。|'a-z'、'A-Z'、'0-9''を含む文字列。|  
|error_id|**nvarchar(36)**|要求に関連付けられているエラーの一意の ID (存在する場合)。|[「トランザクション SQL&#41;&#40;sys.dm_pdw_errors ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md)」を参照してください。エラーが発生しなかった場合は NULL に設定されます。|  
|database_id|**int**|明示的なコンテキストで使用されるデータベースの識別子 (たとえば、USE DB_X)。|[「トランザクション SQL&#41;&#40;sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)の ID 」を参照してください。|  
|command|**nvarchar (4000)**|ユーザーが送信した要求の全文を保持します。|有効なクエリまたは要求テキスト。 4000 バイトを超えるクエリは切り捨てられます。|  
|resource_class|**nvarchar(20)**|この要求に使用されるワークロード・グループ。 |静的リソース クラス</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>動的リソース クラス</br>スモールRC</br>ミディアムRC</br>ラージRC</br>エクスラージ|
|importance|**nvarchar(128)**|要求の実行時の重要度の設定。  これは、このワークロード グループ内の要求と、共有リソースのワークロード グループ間の要求の相対的な重要度です。  分類子で指定された重要度は、ワークロード・グループの重要度設定をオーバーライドします。</br>適用対象: Azure SQL Data Warehouse|NULL</br>low</br>below_normal</br>通常 (デフォルト)</br>above_normal</br>high|
|group_name|**sysname** |リソースを使用する要求の場合、group_nameは、要求が実行されているワークロード・グループの名前です。  要求がリソースを使用しない場合、group_nameは null です。</br>適用対象: Azure SQL Data Warehouse|
|classifier_name|**sysname**|リソースを利用する要求の場合、リソースおよび重要度の割り当てに使用される分類子の名前。||
|resource_allocation_percentage|**10進数(5,2)**|要求に割り当てられたリソースの割合。</br>適用対象: Azure SQL Data Warehouse|
|result_cache_hit|**16 進 数**|完了したクエリで結果セット キャッシュが使用されたかどうかを詳細に示します。  </br>適用対象: Azure SQL Data Warehouse| 1 = 結果セット キャッシュ ヒット </br> 0 = 結果セット キャッシュ ミス </br> 負の値 = 結果セットのキャッシュが使用されなかった理由。  詳細については、「備考」を参照してください。|
||||
  
## <a name="remarks"></a>解説 
 このビューで保持される最大行数については、「[容量の制限](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)」トピックの「メタデータ」セクションを参照してください。

 result_cache_hitは、クエリが結果セット キャッシュを使用するビットマスクです。  この列は[|(ビット単位 OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)1 つ以上の値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|結果セット キャッシュ ヒット|  
|-**0x00**|結果セット のキャッシュ ミス|  
|-**0x01**|データベースで結果セットのキャッシュが無効になります。|  
|-**0x02**|結果セットのキャッシュはセッションで無効になります。 | 
|-**0x04**|クエリのデータ ソースがないため、結果セットのキャッシュは無効になります。|  
|-**0x08**|行レベルのセキュリティ述語のため、結果セットのキャッシュは無効になっています。|  
|-**0x10**|クエリでシステム テーブル、一時テーブル、または外部テーブルを使用しているため、結果セットのキャッシュは無効になります。|  
|-**0x20**|クエリにランタイム定数、ユーザー定義関数、または非決定的関数が含まれているため、結果セットのキャッシュは無効になります。|  
|-**0x40**|結果セットのサイズが 10 GB >見積もりされているため、結果セットのキャッシュは無効になっています。|  
|-**0x80**|結果セットに大きなサイズ (>64 kb) の行が含まれているため、結果セットのキャッシュは無効になります。|  
  
## <a name="permissions"></a>アクセス許可

 VIEW SERVER STATE 権限が必要です。  
  
## <a name="security"></a>Security

 sys.dm_pdw_exec_requests は、データベース固有のアクセス許可に従ってクエリ結果をフィルター処理しません。 VIEW SERVER STATE 権限を持つログインでは、すべてのデータベースの結果クエリ結果を取得できます。  
  
>[!WARNING]  
>攻撃者は sys.dm_pdw_exec_requests を使用して、単に VIEW SERVER STATE 権限を持ち、データベース固有の権限を持たないだけで、特定のデータベース オブジェクトに関する情報を取得できます。  
  
## <a name="see-also"></a>参照

 [SQL データ ウェアハウスおよび並列データ ウェアハウスの動的管理ビュー&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)
