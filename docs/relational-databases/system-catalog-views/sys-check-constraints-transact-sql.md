---
title: sys.check_constraints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.check_constraints
- sys.check_constraints_TSQL
- check_constraints_TSQL
- check_constraints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.check_constraints catalog view
ms.assetid: 940ebc5e-44ba-4dae-8b29-da94f2d1d6c4
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d79720c8e4e966c7f0129371dd6a22be4217f356
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788530"
---
# <a name="syscheckconstraints-transact-sql"></a>sys.check_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  CHECK 制約のあるオブジェクトごとの行を格納**sys.objects.type** = 'C'。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、[sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)を参照してください。|  
|**is_disabled**|**bit**|CHECK 制約は無効です。|  
|**is_not_for_replication**|**bit**|NOT FOR REPLICATION オプションを使用して作成された CHECK 制約です。|  
|**is_not_trusted**|**bit**|システムがすべての行を検証していない CHECK 制約です。|  
|**parent_column_id**|**int**|0 はテーブルレベルの CHECK 制約を示します。<br /><br /> 0 以外の値は、これが、指定された ID 値の列で定義された列レベルの CHECK 制約であることを示します。|  
|**definition**|**nvarchar(max)**|この CHECK 制約を定義する SQL 式です。|  
|**uses_database_collation**|**bit**|制約定義は、適切な評価のために、データベースの既定の照合順序に依存し、値は 1 となります。それ以外の場合は 0 です。 このような依存関係は、データベースの既定の照合順序を変更できないようにします。|  
|**is_system_named**|**bit**|1 = 名前はシステムによって生成されました。<br /><br /> 0 = ユーザー指定の名前。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
