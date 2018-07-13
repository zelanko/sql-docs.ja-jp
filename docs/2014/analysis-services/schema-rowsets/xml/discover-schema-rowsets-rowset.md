---
title: DISCOVER_SCHEMA_ROWSETS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_SCHEMA_ROWSETS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa16f7ff677efd8e39367b9e618bdc95d778b405
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220242"
---
# <a name="discoverschemarowsets-rowset"></a>DISCOVER_SCHEMA_ROWSETS 行セット
  すべての列挙値と、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされている追加のプロバイダー固有の列挙値について、名前、制限、説明、その他の情報を返します。  
  
 呼び出す場合、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッドを`DISCOVER_SCHEMA_ROWSETS`列挙値、 [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)要素、`Discover`メソッドを返します。、`DISCOVER_SCHEMA_ROWSETS`行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 DISCOVER_SCHEMA_ROWSETS 行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`SchemaName`|`DBTYPE_WSTR`||スキーマまたは要求の名前。 この要求は、値を返します、 *RequestTypes*列挙体。|  
|`SchemaGuid`|`DBTYPE_GUID`||スキーマの GUID です。|  
|`Restrictions`|`DBTYPE_HCHAPTER`||プロバイダーによってサポートされている制限の配列。|  
|`Description`|`DBTYPE_WSTR`||スキーマのローカライズ可能な説明。|  
|`RestrictionsMask`|`DBTYPE_UI8`|||  
  
 このスキーマ行セットは並べ替えられません。  
  
 DBSCHEMA_MEMBERS スキーマ行セットに対して 3 つの制限をサポートするプロバイダーの場合、`Restrictions` 配列によって次の結果が返される場合があります。 結果内の要素は、スキーマの列名を表しています。  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_SCHEMA_ROWSETS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`SchemaName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
