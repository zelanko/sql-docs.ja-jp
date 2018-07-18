---
title: MeasureGroupAttributeBinding データ型 (の不一致) (ASSL) |Microsoft Docs
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
- MeasureGroupAttributeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MeasureGroupAttributeBinding data type
ms.assetid: bfe09a95-4e04-4f93-9389-7dd0b4c8f5e4
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 244656b0ae951ec5f8274f11e58153faef80957d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218212"
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>MeasureGroupAttributeBinding データ型 (不一致) (ASSL)
  メジャー グループに含まれているディメンション内の属性の不一致バインドを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[バインド](binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[CubeID](../properties/id-element-assl.md)、 [DatabaseID](../../xmla/xml-elements-properties/id-element-xmla.md)、 [MeasureGroupID](../properties/measuregroupid-element-assl.md)、 [GranularityAttributeID](../properties/attributeid-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)|  
|派生要素|[バインド](../../xmla/xml-elements-properties/binding-element-xmla.md)([バインド](../collections/attributes-element-assl.md)コレクションの XML for Analysis (XMLA)[バッチ](../../xmla/xml-elements-commands/batch-element-xmla.md)と[プロセス](../../xmla/xml-elements-commands/process-element-xmla.md)コマンド)|  
  
## <a name="remarks"></a>コメント  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
