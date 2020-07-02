---
title: dm_os_loaded_modules (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 30aa54e93b30d2067e2ab02ba8d264920724cead
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754134"
---
# <a name="sysdm_os_loaded_modules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  サーバーのアドレス空間に読み込まれたモジュールごとに1行の値を返します。  
  
> [!NOTE]  
>  これをから呼び出すには [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 、 **dm_pdw_nodes_os_loaded_modules**という名前を使用します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary (8)**|プロセス内のモジュールのアドレス。|  
|**file_version**|**varchar (23)**|ファイルのバージョン。 次の形式で表示されます。<br /><br /> x.x:x.x|  
|**product_version**|**varchar (23)**|製品のバージョン。 次の形式で表示されます。<br /><br /> x.x:x.x|  
|**デバック**|**bit**|1 = モジュールは読み込まれたモジュールのデバッグ バージョンです。|  
|**併せ**|**bit**|1 = モジュールにパッチが適用されました。|  
|**リリース**|**bit**|1 = モジュールは読み込まれたモジュールのプレリリース バージョンです。|  
|**private_build**|**bit**|1 = モジュールは読み込まれたモジュールの個人用ビルドです。|  
|**special_build**|**bit**|1 = モジュールは、読み込まれたモジュールの特別なビルドです。|  
|**language**|**int**|モジュールのバージョン情報の言語。|  
|**全社**|**nvarchar(256)**|モジュールを作成した会社の名前。|  
|**description**|**nvarchar(256)**|モジュールの説明。|  
|**name**|**nvarchar(255)**|モジュールの名前。 モジュールの完全パスが含まれます。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティングシステム関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
