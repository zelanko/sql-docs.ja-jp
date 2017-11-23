---
title: "sys.configurations (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.configurations_TSQL
- configurations
- sys.configurations
- configurations_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.configurations catalog view
ms.assetid: c4709ed1-bf88-4458-9e98-8e9b78150441
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 38f44fb8d174d3fa32bea9d97e079fce0c3d1afc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysconfigurations-transact-sql"></a>sys.configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  システムでは、サーバー全体の構成オプションの値ごとに行が含まれています。  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|構成値の一意 ID|  
|**name**|**nvarchar(35)**|構成オプションの名前。|  
|**値**|**sql_variant**|オプションの構成値|  
|**minimum**|**sql_variant**|構成オプションの最小値|  
|**maximum**|**sql_variant**|構成オプションの最大値|  
|**value_in_use**|**sql_variant**|オプションで現在有効な実行値|  
|**説明**|**nvarchar (255)**|構成オプションの説明|  
|**is_dynamic**|**bit**|1 = RECONFIGURE ステートメントの実行時に影響を与える変数|  
|**is_advanced**|**bit**|1 = 変数が表示される場合にのみ、 **advancedoption を表示する**設定されています。|  
  
 すべてのサーバー構成オプションの一覧は、次を参照してください。[サーバー構成オプション &#40;です。SQL Server &#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
> [!NOTE]  
>  データベース レベルの構成オプションについては、次を参照してください。 [ALTER DATABASE SCOPED CONFIGURATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). ソフト NUMA を構成するのを参照してください。[ソフト NUMA &#40;です。SQL Server &#41;](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [サーバー全体の構成に関するカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
