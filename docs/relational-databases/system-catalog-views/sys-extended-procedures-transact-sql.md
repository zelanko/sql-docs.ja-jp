---
title: sys.extended_procedures (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- extended_procedures
- sys.extended_procedures
- sys.extended_procedures_TSQL
- extended_procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.extended_procedures catalog view
ms.assetid: 310e0f87-0044-4fdf-bd12-51a723a74ce6
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: be24a61208f854976b45a7ba927e83a4c87fecb5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysextendedprocedures-transact-sql"></a>sys.extended_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 行で、拡張ストアド プロシージャは、各オブジェクトのデータを含む**sys.objects.type** X を = です。拡張ストアド プロシージャにインストールされているため、**マスター**データベースのみ表示されるデータベースのコンテキストからです。 選択すると、 **sys.extended_procedures**以外のデータベース コンテキストでのビューは空の結果セットを返します。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)です。|  
|**dll_name**|**nvarchar(260)**|この拡張ストアド プロシージャの DLL の名前です (パスを含む)。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
