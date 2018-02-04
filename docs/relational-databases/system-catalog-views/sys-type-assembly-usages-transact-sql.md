---
title: "sys.type_assembly_usages (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.type_assembly_usages
- sys.type_assembly_usages_TSQL
- type_assembly_usages_TSQL
- type_assembly_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.type_assembly_usages catalog view
ms.assetid: 79b8bf25-6e4e-4a07-ae93-7a4e44f65171
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3ce4d7e61fb608e44d5ef9f218449981d7d49c1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="systypeassemblyusages-transact-sql"></a>sys.type_assembly_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アセンブリ参照に対する種類ごとに 1 行のデータを保持します。  
  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**user_type_id**|**int**|種類の ID です。<br /><br /> 型の名前を返すに参加させる、 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログをこの列に表示します。|  
|**assembly_id**|**int**|アセンブリの ID|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スカラー型カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
