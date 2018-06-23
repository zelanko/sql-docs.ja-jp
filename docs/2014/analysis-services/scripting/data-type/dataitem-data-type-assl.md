---
title: DataItem データ型 (ASSL) |Microsoft ドキュメント
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
- DataItem Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataItem
helpviewer_keywords:
- DataItem data type
ms.assetid: f4f5155f-9c3d-49a1-a390-a9c734fafbce
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0d5622ca2cdda5a08bdcfdfd486e44b6fcd8fbf7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073580"
---
# <a name="dataitem-data-type-assl"></a>DataItem データ型 (ASSL)
  列や属性などのデータ アイテムのデータ関連の特性を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataItem>  
   <DataType>...</DataType>  
   <DataSize>...</DataSize>  
   <MimeType>...</MimeType>  
   <NullProcessing>...</NullProcessing>  
   <Trimming>...</Trimming>  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
      <Collation>...</Collation>  
   <Format>...</Format>  
   <Source>...</Source>  
   <Annotations>...</Annotations>  
</DataItem>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../collections/annotations-element-assl.md)、[照合](../properties/collation-element-assl.md)、 [DataSize](../properties/datasize-element-assl.md)、 [DataType](../properties/datatype-element-assl.md)、[形式](../properties/format-element-assl.md)、 [InvalidXmlCharacters](../properties/invalidxmlcharacters-element-assl.md)、 [MimeType](../properties/mimetype-element-assl.md)、 [NullProcessing](../properties/nullprocessing-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)、[トリミング](../properties/trimming-element-assl.md)|  
|派生要素|「コメント」の表を参照|  
  
## <a name="remarks"></a>コメント  
 `DataItem` データ型は、メジャー、属性キー、属性名などのバインド可能なデータ アイテムで使用されます。 属性名は文字列でなければならないなど、関連する詳細および適用される既定値は、使用法によって異なります。  
  
 インスタンス[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データ型の特定のセットのみを受け入れます。 他のデータ型を使用すると、有効なデータ型に暗黙的に変換されるのではなく、エラーになります。  
  
 次の表は、`DataItem` 型の要素を示しています。  
  
|親要素|`DataItem` 型の要素|コメント|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../objects/column-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)または[AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrollupcolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)または[AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/customrolluppropertiescolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)または[AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/keycolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)、 [AttributeBinding](attributebinding-data-type-assl.md)または[TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/namecolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)または[AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/skippedlevelscolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)または[AttributeBinding](attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../objects/unaryoperatorcolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)または[AttributeBinding](attributebinding-data-type-assl.md)|  
|[メジャー](../objects/measure-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|`Source` 要素、`DataItem`型でなければなりません[RowBinding](rowbinding-data-type-assl.md)、 [ColumnBinding](binding-data-type-assl.md)、 [MeasureBinding](measurebinding-data-type-assl.md)、または[CubeDimensionBinding](dimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[KeyColumn](../objects/keycolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)、 [AttributeBinding](attributebinding-data-type-assl.md)または[InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[KeyColumn](../objects/keycolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[[Namecolumn]](../objects/namecolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/foreignkeycolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)|  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DataItem>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  