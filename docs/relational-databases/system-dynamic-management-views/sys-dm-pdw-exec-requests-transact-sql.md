---
title: sys _pdw_exec_requests (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
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
ms.openlocfilehash: 72af3975378b2450e51b3880e8814705bb514c1a
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811400"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys _pdw_exec_requests (Transact-sql)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  現在または最近アクティブになっているすべて[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]の要求に関する情報を保持します。 要求/クエリごとに1行が一覧表示されます。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|このビューのキー。 要求に関連付けられている一意の数値 ID。|システム内のすべての要求間で一意です。|  
|session_id|**nvarchar(32)**|このクエリが実行されたセッションに関連付けられている一意の数値 ID。 「 [_Pdw_exec_sessions &#40;&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)」を参照してください。||  
|status|**nvarchar(32)**|要求の現在の状態。|' Running '、' 中断 '、' Completed '、' Canceled '、' Failed '。|  
|submit_time|**datetime**|要求が実行のために送信された時刻。|有効な**datetime**が、現在の時刻と start_time の値より小さいか等しい。|  
|start_time|**datetime**|要求の実行が開始された時刻。|キューに置かれた要求の場合は NULL です。それ以外の場合は、有効な**datetime**が現在の時刻以下であることを指定します。|  
|end_compile_time|**datetime**|エンジンが要求のコンパイルを完了した時刻。|まだコンパイルされていない要求の場合は NULL です。それ以外の場合、有効な**datetime**は start_time より小さく、現在の時刻以下です。|
|end_time|**datetime**|要求の実行が完了、失敗、または取り消された時刻。|キューに置かれた要求またはアクティブな要求の場合は Null です。それ以外の場合は、有効な**datetime**が現在の時刻以下であることを指定します。|  
|total_elapsed_time|**int**|要求が開始されてから経過した時間 (ミリ秒単位)。|0 ~ start_time と end_time の間の差。</br></br> Total_elapsed_time では、整数の最大値を超えると、total_elapsed_time 引き続き、最大値になります。 この条件により、"最大値を超えました。" という警告が生成されます。</br></br> ミリ秒単位の最大値は、24.8 日と同じです。|  
|ラベル●らべる○|**nvarchar (255)**|いくつかの SELECT クエリステートメントに関連付けられているオプションのラベル文字列。|' A-z '、' A-z '、' 0-9 '、' _ ' を含む任意の文字列。|  
|error_id|**nvarchar(36)**|要求に関連付けられているエラーの一意の ID (存在する場合)。|「 [ &#40;_Pdw_errors transact-sql&#41;」を](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md)参照してください。エラーが発生しなかった場合は、NULL に設定します。|  
|database_id|**int**|明示的なコンテキストで使用されるデータベースの識別子 (たとえば、DB_X を使用します)。|「 [Sys &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)」の「ID」を参照してください。|  
|command|**nvarchar (4000)**|ユーザーによって送信された要求の完全なテキストを保持します。|任意の有効なクエリまたは要求テキスト。 4000バイトを超えるクエリは切り捨てられます。|  
|resource_class|**nvarchar(20)**|この要求のリソースクラス。 「 **Concurrency_slots_used**の関連する[_pdw_resource_waits &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)」を参照してください。  リソースクラスの詳細については、「[リソースクラス & ワークロード管理](https://docs.microsoft.com/azure/sql-data-warehouse/resource-classes-for-workload-management)」を参照してください。 |静的リソース クラス</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>動的リソース クラス</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance|**nvarchar(32)**|要求がと共に送信されたときの重要度を設定します。 重要度が低い要求が送信されると、その下位の要求は保留状態のままになります。  重要度の高い要求は、前に送信された重要度の低い要求の前に実行されます。  重要度の詳細については、「[ワークロードの重要度](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-workload-importance)」を参照してください。  |NULL</br>low</br>below_normal</br>標準 (既定値)</br>above_normal</br>high|
|group_name| |内部使用のために予約済みです。</br>適用対象:Azure SQL Data Warehouse|
|resource_allocation_percentage| |内部使用のために予約済みです。</br>適用対象:Azure SQL Data Warehouse|
|result_set_cache|**bit**|完了したクエリの結果がキャッシュヒット (1) であるかどうか、またはそれ以外 (0) であるかどうかを詳細に説明します。|0、1|
||||
  
 このビューで保持される最大行数の詳細については、「[容量制限](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)」トピックの「メタデータ」セクションを参照してください。   
  
## <a name="permissions"></a>アクセス許可

 VIEW SERVER STATE 権限が必要です。  
  
## <a name="security"></a>セキュリティ

 _pdw_exec_requests では、データベース固有のアクセス許可に従ってクエリ結果がフィルター処理されません。 VIEW SERVER STATE 権限を持つログインは、すべてのデータベースの結果のクエリ結果を取得できます。  
  
>[!WARNING]  
>攻撃者は、_pdw_exec_requests を使用して特定のデータベースオブジェクトに関する情報を取得できます。これを行うには、VIEW SERVER STATE 権限を持ち、データベース固有の権限がないことが必要です。  
  
## <a name="see-also"></a>参照

 [SQL Data Warehouse および並列データウェアハウスの動的管理&#40;ビュー transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md) 
