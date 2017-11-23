---
title: "sys.sysservers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e05b06dd6a37f6330f715b374e3fe46515c3f37d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが OLE DB データ ソースとしてアクセスできるサーバーごとに、1 行のデータを格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**srvid**|**smallint**|リモート サーバーの ID (ローカル専用)。|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**済み**|**sysname**|サーバー名。|  
|**srvproduct**|**sysname**|リモート サーバーの製品名。|  
|**providername**|**nvarchar (128)**|サーバーへのアクセスを提供する OLE DB プロバイダー名。|  
|**データ ソース**|**nvarchar (4000)**|OLE DB データ ソース値。|  
|**場所**|**nvarchar (4000)**|OLE DB ロケーション値。|  
|**providerstring**|**nvarchar (4000)**|OLE DB プロバイダー文字列値。|  
|**schemadate**|**datetime**|この行が前回更新された日付。|  
|**topologyx**|**int**|使用されていません。|  
|**topologyy**|**int**|使用されていません。|  
|**カタログ**|**sysname**|OLE DB プロバイダーに接続するときに使用するカタログ。|  
|**srvcollation**|**sysname**|サーバーの照合順序。|  
|**connecttimeout**|**int**|サーバー接続に対するタイムアウトの設定。|  
|**querytimeout**|**int**|サーバーに対するクエリのタイムアウトの設定。|  
|**srvnetname**|**char (30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**bit**|1 = サーバーはリモート サーバー。<br /><br /> 0 = サーバーはリンク サーバー。|  
|**rpc**|**bit**|1 =  **sp_serveroption@rpc**  'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@rpc**  'éý' **false**または**オフ**です。|  
|**pub**|**bit**|1 =  **sp_serveroption@pub**  'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@pub**  'éý' **false**または**オフ**です。|  
|**sub**|**bit**|1 =  **sp_serveroption@sub**  'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@sub**  'éý' **false**または**オフ**です。|  
|**dist**|**bit**|1 =  **sp_serveroption@dist**  'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@dist**  'éý' **false**または**オフ**です。|  
|**dpub**|**bit**|1 =  **sp_serveroption@dpub**  'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@dpub**  'éý' **false**または**オフ**です。|  
|**rpcout**|**bit**|1 =  **sp_serveroption@rpcアウト**'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@rpcアウト**'éý' **false**または**オフ**です。|  
|**データ アクセス**|**bit**|1 =  **sp_serveroption@dataアクセス**'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@dataアクセス**'éý' **false**または**オフ**です。|  
|**collationcompatible**|**bit**|1 =  **sp_serveroption@collation互換性**'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@collation互換性**'éý' **false**または**オフ**です。|  
|**システム**|**bit**|1 =  **sp_serveroption@system**  'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@system**  'éý' **false**または**オフ**です。|  
|**useremotecollation**|**bit**|1 =  **sp_serveroption@remote照合順序**'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@remote照合**'éý' **false**または**オフ**です。|  
|**lazyschemavalidation**|**bit**|1 =  **sp_serveroption@lazyスキーマ検証**'éý' **true**または**で**です。<br /><br /> 0 =  **sp_serveroption@lazyスキーマ検証**'éý' **false**または**オフ**です。|  
|**照合順序**|**sysname**|サーバー照合順序によって設定された**sp_serveroption@collation名前**です。|  
|**nonsqlsub**|bit|0 = サーバーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス。<br /><br /> 1 = サーバーは、のインスタンスではありません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
