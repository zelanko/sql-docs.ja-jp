---
title: DimensionAttributeBinding データ型 (の不一致) (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- DimensionAttributeBinding Data Type (out-of-line)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DimensionAttributeBinding data type
ms.assetid: d8ec77a9-749f-4b08-8d56-8b6514a70248
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3a17631b80bcbbb5dc9d363b45e3cd8ac8a16405
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="dimensionattributebinding-data-type-out-of-line-assl"></a>DimensionAttributeBinding データ型 (不一致) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]ディメンション内の属性の不一致のバインドを表す派生データ型を定義します。  
  
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
  
|特性|Description|  
|--------------------|-----------------|  
|基本データ型|[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)、 [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md)、 [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md)、 [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)、 [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)、 [翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|派生要素|[バインド](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md)([バインド](../../../analysis-services/scripting/collections/attributes-element-assl.md)コレクションの XML for Analysis (XMLA)[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)と[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)コマンド)|  
  
## <a name="remarks"></a>解説  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとのバインド &#40;です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
