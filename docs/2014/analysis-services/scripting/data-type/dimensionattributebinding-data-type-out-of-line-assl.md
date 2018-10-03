---
title: DimensionAttributeBinding データ型 (の不一致) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DimensionAttributeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DimensionAttributeBinding data type
ms.assetid: d8ec77a9-749f-4b08-8d56-8b6514a70248
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d649dcfc5070d0c60a2ab3cea421e5c8b0c328b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197764"
---
# <a name="dimensionattributebinding-data-type-out-of-line-assl"></a>DimensionAttributeBinding データ型 (不一致) (ASSL)
  ディメンション内の属性の不一致バインドを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <DimensionID>...</DimensionID>  
   <AttributeID>...</AttributeID>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <Translations>...</Translations>  
</DimensionAttributeBinding>  
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
|子要素|[AttributeID](../properties/id-element-assl.md)、 [DatabaseID](../../xmla/xml-elements-properties/id-element-xmla.md)、 [DimensionID](../properties/dimensionid-element-assl.md)、 [KeyColumns](../collections/columns-element-assl.md)、 [NameColumn](../objects/column-element-assl.md)、[翻訳](../collections/translations-element-assl.md)|  
|派生要素|[バインド](../../xmla/xml-elements-properties/binding-element-xmla.md)([バインド](../collections/attributes-element-assl.md)コレクションの XML for Analysis (XMLA)[バッチ](../../xmla/xml-elements-commands/batch-element-xmla.md)と[プロセス](../../xmla/xml-elements-commands/process-element-xmla.md)コマンド)|  
  
## <a name="remarks"></a>コメント  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
