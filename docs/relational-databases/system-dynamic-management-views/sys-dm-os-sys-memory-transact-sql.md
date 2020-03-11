---
title: dm_os_sys_memory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_sys_memory
- sys.dm_os_sys_memory_TSQL
- sys.dm_os_sys_memory
- dm_os_sys_memory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_memory dynamic management view
ms.assetid: 1ca58814-1caa-44c1-b307-ff0bdcbbef62
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 891ae8c4f21d0a38302a7213aab22b8a70e855ba
ms.sourcegitcommit: 7008c7fe451a20d6610e40bb8f61dece86c0f17e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79027947"
---
# <a name="sysdm_os_sys_memory-transact-sql"></a>dm_os_sys_memory (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  オペレーティングシステムからメモリ情報を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、オペレーティングシステムレベルの外部メモリ条件と、基になるハードウェアの物理的な制限によって制限され、応答します。 システム全体の状態を調査することは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリ使用量を評価するうえで重要な要素です。  
  
> [!NOTE]  
>  またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]これを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_os_sys_memory**という名前を使用します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**total_physical_memory_kb**|**bigint**|オペレーティングシステムで使用できる物理メモリの合計サイズ (KB 単位)。|  
|**available_physical_memory_kb**|**bigint**|使用可能な物理メモリのサイズ (KB 単位)。|  
|**total_page_file_kb**|**bigint**|オペレーティング システムによって報告されたコミット制限のサイズ (KB 単位)。|  
|**available_page_file_kb**|**bigint**|使用されていないページファイルの合計サイズ (KB 単位)。|  
|**system_cache_kb**|**bigint**|システム キャッシュ メモリの合計サイズ (KB 単位)。|  
|**kernel_paged_pool_kb**|**bigint**|ページ カーネル プールの合計サイズ (KB 単位)。|  
|**kernel_nonpaged_pool_kb**|**bigint**|非ページカーネルプールの合計サイズ (KB 単位)。|  
|**system_high_memory_signal_state**|**bit**|システムの高メモリ リソース通知の状態。 この値が 1 の場合、Windows によって高メモリ シグナルが設定されていることを意味します。 詳細については、MSDN ライブラリの「 [CreateMemoryResourceNotification](https://go.microsoft.com/fwlink/?LinkId=82427) 」を参照してください。|  
|**system_low_memory_signal_state**|**bit**|システムのメモリ不足のリソース通知の状態。 値が1の場合は、メモリ不足のシグナルが Windows によって設定されていることを示します。 詳細については、MSDN ライブラリの「 [CreateMemoryResourceNotification](https://go.microsoft.com/fwlink/?LinkId=82427) 」を参照してください。|  
|**system_memory_state_desc**|**nvarchar(256)**|メモリ状態の説明。 次の表を参照してください。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
|条件|Value|  
|---------------|-----------|  
|system_high_memory_signal_state = 1<br /><br /> および<br /><br /> system_low_memory_signal_state = 0|使用可能な物理メモリが十分に存在します。|  
|system_high_memory_signal_state = 0<br /><br /> および<br /><br /> system_low_memory_signal_state = 1|使用可能な物理メモリが不足しています。|  
|system_high_memory_signal_state = 0<br /><br /> および<br /><br /> system_low_memory_signal_state = 0|物理メモリの使用量が安定しています。|  
|system_high_memory_signal_state = 1<br /><br /> および<br /><br /> system_low_memory_signal_state = 1|物理メモリの状態が遷移中です<br /><br /> 高シグナルと低シグナルが同時にオンになることはありません。 ただし、オペレーティングシステムレベルでの迅速な変更により、両方の値がユーザーモードアプリケーションに表示される可能性があります。 両方のシグナルがオンのように見えるとき、その状態は遷移中の状態と解釈されます。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティングシステム関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


