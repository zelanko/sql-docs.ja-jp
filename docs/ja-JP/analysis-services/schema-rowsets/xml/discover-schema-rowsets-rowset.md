---
title: DISCOVER_SCHEMA_ROWSETS 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DISCOVER_SCHEMA_ROWSETS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fafe6ed5d5a81cb73ddc53a68408e4548ac92699
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="discoverschemarowsets-rowset"></a>DISCOVER_SCHEMA_ROWSETS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  すべての列挙値と、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされている追加のプロバイダー固有の列挙値について、名前、制限、説明、その他の情報を返します。  
  
 呼び出す場合は、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドを**DISCOVER_SCHEMA_ROWSETS**の列挙値に、 [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md)要素、 **Discover**メソッドを返します、 **DISCOVER_SCHEMA_ROWSETS**行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 DISCOVER_SCHEMA_ROWSETS 行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**スキーマ名**|**DBTYPE_WSTR**||スキーマまたは要求の名前。 この要求の値が返されます、 *RequestTypes*列挙します。|  
|**される**|**DBTYPE_GUID 型**||スキーマの GUID です。|  
|**制限事項**|**DBTYPE_HCHAPTER**||プロバイダーによってサポートされている制限の配列。|  
|**Description**|**DBTYPE_WSTR**||スキーマのローカライズ可能な説明。|  
|**RestrictionsMask**|**DBTYPE_UI8**|||  
  
 このスキーマ行セットは並べ替えられません。  
  
 DBSCHEMA_MEMBERS スキーマ行セットの 3 つの制限をサポートするプロバイダーを**制限**配列は、次の結果を返す場合があります。 結果内の要素は、スキーマの列名を表しています。  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_SCHEMA_ROWSETS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**スキーマ名**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
