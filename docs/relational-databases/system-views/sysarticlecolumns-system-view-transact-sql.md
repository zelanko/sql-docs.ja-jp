---
title: sysarticlecolumns (システムビュー) (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10467dfa991efbed27941ba31424057b721527d1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750132"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (システム ビュー) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **Sysarticlecolumns**ビューでは、パブリッシュされたアーティクルの列に関する追加情報が公開されます。 このビューは、ディストリビューション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルを識別します。|  
|**colid**|**int**|アーティクル内の列を識別します。|  
|**is_udt**|**int**|列がユーザー定義データ型 (UDT) 列であるかどうかを示します。 値**1**は UDT 列を示します。|  
|**is_xml**|**int**|列が**xml**列かどうかを示します。 値**1**は**xml**列を示します。|  
|**is_max**|**int**|列が大きな値のデータ型の列 (**varchar (max)**、 **nvarchar (max)** 、または**varbinary (max)**) であるかどうかを示します。 値**1**は大きな値の列を示します。|  
  
## <a name="see-also"></a>関連項目  
 [sp_articlecolumn &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-sql&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
