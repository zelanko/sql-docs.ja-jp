---
title: dm_os_performance_counters (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c7b4d78f73af003e93bc662f10f1f95acda2b6a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265711"
---
# <a name="sysdm_os_performance_counters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  サーバーによって管理されているパフォーマンス カウンターごとに 1 つの行を返します。 各パフォーマンスカウンターの詳細については、「 [SQL Server オブジェクトの使用](../../relational-databases/performance-monitor/use-sql-server-objects.md)」を参照してください。  
  
> [!NOTE]  
>  またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]これを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_os_performance_counters**という名前を使用します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|このカウンターが属するカテゴリ。|  
|**counter_name**|**nchar(128)**|カウンターの名前。 カウンターに関する詳細情報を取得するには、[[オブジェクト SQL Server 使用](../../relational-databases/performance-monitor/use-sql-server-objects.md)するカウンターの一覧から選択するトピックの名前を指定します。 |  
|**instance_name**|**nchar(128)**|カウンターの特定のインスタンスの名前。 多くの場合、データベース名が含まれます。|  
|**cntr_value**|**bigint**|カウンターの現在の値。<br /><br /> **注:** 秒単位のカウンターの場合、この値は累積されます。 レート値は、不連続の時間間隔で値をサンプリングすることによって計算する必要があります。 2つの連続するサンプル値の違いは、使用された時間間隔のレートと同じです。|  
|**cntr_type**|**int**|Windows パフォーマンスアーキテクチャで定義されているカウンターの種類。 パフォーマンスカウンターの種類の詳細については、ドキュメントの「 [WMI パフォーマンスカウンターの種類](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-performance-counter-types)」または Windows Server のドキュメントを参照してください。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール インスタンスで Windows オペレーティング システムのパフォーマンス カウンターが表示されない場合は、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを使用して、パフォーマンス カウンターが無効になっていることを確認します。  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 戻り値が 0 行の場合、パフォーマンス カウンターが無効であることを意味します。 その場合は、セットアップ ログを参照して、エラー 3409 "このインスタンスの sqlctr.ini を再インストールし、インスタンス ログイン アカウントに適切なレジストリ権限が許可されていることを確認してください" を探す必要があります。  これは、パフォーマンス カウンターが無効であったことを示します。 3409エラーの直前に発生したエラーは、パフォーマンスカウンターの有効化の失敗の根本原因を示しています。 セットアップログファイルの詳細については、「 [SQL Server セットアップログファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)」を参照してください。  
  
## <a name="permission"></a>アクセス許可

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   
 
## <a name="examples"></a>使用例  
 次の例では、パフォーマンスカウンターの値を返します。  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>参照  
  [SQL Server オペレーティングシステム関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


