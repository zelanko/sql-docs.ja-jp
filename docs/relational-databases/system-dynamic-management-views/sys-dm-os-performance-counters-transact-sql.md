---
title: sys.dm_os_performance_counters (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_performance_counters
- sys.dm_os_performance_counters_TSQL
- dm_os_performance_counters_TSQL
- sys.dm_os_performance_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_performance_counters dynamic management view
ms.assetid: a1c3e892-cd48-40d4-b6be-2a9246e8fbff
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8613e6acb933cdf6d898799950649023d075b91c
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmosperformancecounters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  サーバーで管理されているパフォーマンス カウンターごとに 1 行のデータを返します。 各パフォーマンス カウンターの詳細については、次を参照してください。 [SQL Server オブジェクトの使用](../../relational-databases/performance-monitor/use-sql-server-objects.md)です。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_performance_counters**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|カウンターが属するカテゴリ。|  
|**counter_name**|**nchar(128)**|カウンターの名前です。 これでカウンターの一覧から選択するトピックの名前は、の詳細については、カウンターを取得する[SQL Server オブジェクトの使用](../../relational-databases/performance-monitor/use-sql-server-objects.md)です。 |  
|**instance_name**|**nchar(128)**|カウンターの特定インスタンスの名前。 多くの場合、データベース名が格納されます。|  
|**cntr_value**|**bigint**|カウンターの現在の値。<br /><br /> **注:** 1 秒あたりのカウンターでは、この値は累積されます。 レート値は、連続しない間隔で値をサンプリングして算出する必要があります。 2 つの連続するサンプル値の間隔は、使用される間隔のレートと同じです。|  
|**cntr_type**|**int**|Windows パフォーマンス アーキテクチャによって定義されるカウンターの種類。 参照してください[WMI パフォーマンス カウンターの種類](http://msdn2.microsoft.com/library/aa394569.aspx)MSDN またはパフォーマンス カウンターの種類の詳細については、Windows Server のドキュメントです。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール インスタンスで Windows オペレーティング システムのパフォーマンス カウンターが表示されない場合は、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを使用して、パフォーマンス カウンターが無効になっていることを確認します。  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 戻り値が 0 行の場合、パフォーマンス カウンターが無効であることを意味します。 その場合は、セットアップ ログを参照して、エラー 3409 "このインスタンスの sqlctr.ini を再インストールし、インスタンス ログイン アカウントに適切なレジストリ権限が許可されていることを確認してください" を探す必要があります。  これは、パフォーマンス カウンターが無効であったことを示します。 3409 エラーの直前に示されるエラーは、パフォーマンス カウンターの有効化に失敗した根本の原因を示しています。 セットアップ ログ ファイルの詳細については、次を参照してください。[ビューと読み取り SQL Server セットアップ ログ ファイル](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)です。  
  
## <a name="permission"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
 
## <a name="examples"></a>使用例  
 次の例では、パフォーマンス カウンターの値を返します。  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


