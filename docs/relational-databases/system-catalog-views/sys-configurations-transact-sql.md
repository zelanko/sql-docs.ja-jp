---
title: sys. 構成 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.configurations_TSQL
- configurations
- sys.configurations
- configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.configurations catalog view
ms.assetid: c4709ed1-bf88-4458-9e98-8e9b78150441
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9eb9ced4e010001f42e106ce8b1903e029f2f1c4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68109564"
---
# <a name="sysconfigurations-transact-sql"></a>sys.configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  システム内のサーバー全体の構成オプション値ごとに1行の値を格納します。  

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|構成値の一意の ID。|  
|**name**|**nvarchar(35)**|構成オプションの名前。|  
|**value**|**sql_variant**|このオプションの値を構成しました。|  
|**以降**|**sql_variant**|構成オプションの最小値。|  
|**個**|**sql_variant**|構成オプションの最大値。|  
|**value_in_use**|**sql_variant**|オプションで現在有効な実行値|  
|**記述**|**nvarchar(255)**|構成オプションの説明|  
|**is_dynamic**|**bit**|1 = 再構成ステートメントが実行されたときに有効になる変数です。|  
|**is_advanced**|**bit**|1 = 変数は、 **show advancedoption**が設定されている場合にのみ表示されます。|  
  
 すべてのサーバー構成オプションの一覧については、「[サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)」を参照してください。  
  
> [!NOTE]  
>  データベースレベルの構成オプションについては、「 [ALTER DATABASE スコープ構成 &#40;transact-sql&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。 ソフト NUMA を構成するには、「[ソフト numa &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [サーバー全体の構成のカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
