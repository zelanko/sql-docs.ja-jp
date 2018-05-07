---
title: sys.system_components_surface_area_configuration (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.system_components_surface_area_configuration_TSQL
- system_components_surface_area_configuration
- system_components_surface_area_configuration_TSQL
- sys.system_components_surface_area_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_components_surface_area_configuration catalog view
ms.assetid: d9920008-3387-4f9e-8f21-47473f2ba04f
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9612341074b70b688d7333c95ebce3acc0ea1706
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syssystemcomponentssurfaceareaconfiguration-transact-sql"></a>sys.system_components_surface_area_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セキュリティ構成コンポーネントによって有効または無効にできる、実行可能なシステム オブジェクトごとに 1 行のデータを返します。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**component_name**|**sysname**|コンポーネントの名前。 キーワード照合順序 Latin1_General_CI_AS_KS_WS が使用されます。 NULL 値は許容されません。|  
|**database_name**|**sysname**|オブジェクトを含むデータベース。 キーワード照合順序 Latin1_General_CI_AS_KS_WS が使用されます。 次のいずれかを指定する必要があります。<br /><br /> **master**<br /><br /> **msdb**<br /><br /> **mssqlsystemresource**|  
|**schema_name**|**sysname**|オブジェクトを含むスキーマ。 キーワード照合順序 Latin1_General_CI_AS_KS_WS が使用されます。 NULL 値は許容されません。|  
|**object_name**|**sysname**|オブジェクトの名前。 キーワード照合順序 Latin1_General_CI_AS_KS_WS が使用されます。 NULL 値は許容されません。|  
|**状態**|**tinyint**|0 = 無効<br /><br /> 1 = 有効|  
|**type**|**char(2)**|オブジェクトの種類です。 次のいずれかになります。<br /><br /> P = SQL_STORED_PROCEDURE<br /><br /> PC = CLR_STORED_PROCEDURE<br /><br /> FN = SQL_SCALAR_FUNCTION<br /><br /> FS = CLR_SCALAR_FUNCTION<br /><br /> FT = CLR_TABLE_VALUED_FUNCTION<br /><br /> IF = SQL_INLINE_TABLE_VALUED_FUNCTION<br /><br /> TF = SQL_TABLE_VALUED_FUNCTION<br /><br /> X = EXTENDED_STORED_PROCEDURE|  
|**type_desc**|**nvarchar(60)**|オブジェクトの種類の表示名の説明。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
