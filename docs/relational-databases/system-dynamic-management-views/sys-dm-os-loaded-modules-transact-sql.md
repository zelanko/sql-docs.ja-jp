---
title: sys.dm_os_loaded_modules (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 607ed0e3e7244951acbdd52177948cbc133b7997
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーのアドレス空間に読み込まれたモジュールごとに 1 行のデータを返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_loaded_modules**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|プロセス内のモジュールのアドレス。|  
|**file_version**|**varchar(23)**|ファイルのバージョン。 次の形式で表示されます。<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|製品のバージョンです。 次の形式で表示されます。<br /><br /> x.x:x.x|  
|**debug**|**bit**|1 = モジュールは読み込まれたモジュールのデバッグ バージョンです。|  
|**修正プログラムを適用**|**bit**|1 = モジュールは修正済みです。|  
|**プレリリース版**|**bit**|1 = モジュールは読み込まれたモジュールのプレリリース バージョンです。|  
|**private_build**|**bit**|1 = モジュールは読み込まれたモジュールの個人用ビルドです。|  
|**special_build**|**bit**|1 = モジュールは読み込まれたモジュールの特別なビルドです。|  
|**言語**|**int**|モジュールのバージョン情報の言語。|  
|**company**|**nvarchar (256)**|モジュールを作成した会社名。|  
|**説明**|**nvarchar (256)**|モジュールの説明。|  
|**name**|**nvarchar (255)**|モジュールの名前。 モジュールの完全なパスを含みます。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
