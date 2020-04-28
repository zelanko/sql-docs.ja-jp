---
title: xml_schema_wildcard_namespaces (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xml_schema_wildcard_namespaces_TSQL
- xml_schema_wildcard_namespaces
- sys.xml_schema_wildcard_namespaces_TSQL
- sys.xml_schema_wildcard_namespaces
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_wildcard_namespaces catalog view
ms.assetid: a3caa932-41c7-48a9-9b2d-ff090afbb66b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d1085968e76771539c0fa439bc35ed86540dcbe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68109461"
---
# <a name="sysxml_schema_wildcard_namespaces-transact-sql"></a>xml_schema_wildcard_namespaces (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML スキーマワイルドカードの列挙された名前空間ごとに1行の値を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|このが適用される XML スキーマコンポーネント (ワイルドカード) の ID。|  
|**namespace**|**nvarchar (4000)**|XML ワイルドカードによって使用される名前空間の名前または URI。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Xml スキーマ &#40;XML 型システム&#41; カタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
