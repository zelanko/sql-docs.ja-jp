---
title: sys.dm_pdw_exec_requests (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/19/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 09ec22504cce0439d6d3f23360586fb0b41ee0c8
ms.sourcegitcommit: f8fced37f3fe5c45b2b97219d378137afd68cf76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58198191"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  現在または最近アクティブになってすべての要求に関する情報を保持[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。 要求/クエリごとに 1 行が一覧表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|このビューのキー。 要求に関連付けられている一意の数値 ID です。|システム内のすべての要求間で一意です。|  
|session_id|**nvarchar(32)**|このクエリが実行されたセッションに関連付けられた一意の数値 ID です。 参照してください[sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)します。||  
|status|**nvarchar(32)**|要求の現在の状態。|実行中 ' '、'中断'、'完了'、'キャンセル'、'失敗' です。|  
|submit_time|**datetime**|実行の要求が送信された時刻。|有効な**datetime**より小さいか等しい start_time と現在の時刻。|  
|start_time|**datetime**|要求の実行が開始された時刻。|キューに置かれた要求の場合は NULLそれ以外の場合、有効な**datetime**小さいまたは現在の時刻と同じです。|  
|end_compile_time|**datetime**|エンジンが、要求のコンパイルを完了した時刻。|まだコンパイルされていない要求の場合は NULLそれ以外の場合、有効な**datetime** start_time よりも小さいと、現在の時刻。|
|end_time|**datetime**|時間を要求の実行完了、失敗、またはが取り消されました。|キューまたはアクティブな要求の場合は nullそれ以外の場合、有効な**datetime**小さいまたは現在の時刻と同じです。|  
|total_elapsed_time|**int**|ミリ秒単位で、要求を開始からの実行で経過時間。|0 ~ start_time と end_time の違い範囲。</br></br> Total_elapsed_time では、整数の最大値を超えている場合、最大値になります total_elapsed_time では引き続きします。 この状態が"、最大値を超過しました"警告を生成します。</br></br> ミリ秒単位で最大の値は 24.8 日と同じです。|  
|ラベル●らべる○|**nvarchar (255)**|いくつかのクエリの SELECT ステートメントに関連付けられている省略可能なラベル文字列。|任意の文字列を含む ' a ~ z'、' A ~ Z'、' 0-9'、'_' です。|  
|error_id|**nvarchar(36)**|存在する場合、要求に関連するエラーの一意の ID。|参照してください[sys.dm_pdw_errors &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); エラーが発生していない場合は NULL に設定します。|  
|database_id|**int**|コンテキストの明示的な (使用 DB_X など) によって使用されるデータベースの識別子。|内の ID を参照してください。 [sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)します。|  
|command|**nvarchar (4000)**|ユーザーによって送信されると、要求の完全なテキストを保持します。|有効なクエリまたは要求テキスト。 4,000 バイトより長いクエリは、切り捨てられます。|  
|resource_class|**nvarchar(20)**|この要求のリソース クラスです。 関連する参照**concurrency_slots_used**で[sys.dm_pdw_resource_waits &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)します。  リソース クラスの詳細については、次を参照してください[リソース クラスとワークロード管理。](https://docs.microsoft.com/azure/sql-data-warehouse/resource-classes-for-workload-management) |静的リソース クラス</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br></br>動的リソース クラス</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|重要度 (SQL DW Gen2 のプレビュー)|**nvarchar(32)**|要求を設定する重要度が送信されました。 重要度が低い要求は重要度の高い要求が送信された場合に、一時停止状態でキューに置かれます。  重要度の高い要求は、先に送信された下の重要度要求する前に実行されます。  重要度の詳細については、次を参照してください。[ワークロードの重要度](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-workload-importance)します。  |NULL</br>low</br>below_normal</br>標準</br>しなく</br>high|
  
 このビューで保持される行の最大数については、「最小値と最大値」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]します。  
  
## <a name="permissions"></a>アクセス許可

 VIEW SERVER STATE 権限が必要です。  
  
## <a name="security"></a>セキュリティ

 sys.dm_pdw_exec_requests は、データベース固有のアクセス許可に従ってクエリの結果をフィルター処理しません。 VIEW SERVER STATE 権限を持つログインでも、結果をすべてのデータベースのクエリ結果を得ることができます。  
  
>[!WARNING]  
>攻撃者は、sys.dm_pdw_exec_requests を使用して、データベース固有のアクセス許可がないと VIEW SERVER STATE 権限があるだけでは、特定のデータベース オブジェクトに関する情報を取得します。  
  
## <a name="see-also"></a>参照

 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md) 
