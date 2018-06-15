---
title: DataItem データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d1cd797cb0720768856d1845244293ba33ee7e9d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036853"
---
# <a name="dataitem-data-type-assl"></a>DataItem データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[照合](../../../analysis-services/scripting/properties/collation-element-assl.md)、 [DataSize](../../../analysis-services/scripting/properties/datasize-element-assl.md)、 [DataType](../../../analysis-services/scripting/properties/datatype-element-assl.md)、[形式](../../../analysis-services/scripting/properties/format-element-assl.md)、 [InvalidXmlCharacters](../../../analysis-services/scripting/properties/invalidxmlcharacters-element-assl.md)、 [MimeType](../../../analysis-services/scripting/properties/mimetype-element-assl.md)、 [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)、[トリミング](../../../analysis-services/scripting/properties/trimming-element-assl.md)|  
|派生要素|「コメント」の表を参照|  
  
## <a name="remarks"></a>解説  
 **DataItem**バインドできるデータ項目以外の場合は、メジャー、属性キーと属性名のデータ型を使用します。 属性名は文字列でなければならないなど、関連する詳細および適用される既定値は、使用法によって異なります。  
  
 インスタンス[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データ型の特定のセットのみを受け入れます。 他のデータ型を使用すると、有効なデータ型に暗黙的に変換されるのではなく、エラーになります。  
  
 次の表に、型の要素**DataItem**です。  
  
|親要素|型の要素**DataItem**|コメント|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|[CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)または[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[CustomRollupColumn](../../../analysis-services/scripting/objects/customrollupcolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)または[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[CustomRollupPropertiesColumn](../../../analysis-services/scripting/objects/customrolluppropertiescolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)または[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)または[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[[Namecolumn]](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)または[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[SkippedLevelsColumn](../../../analysis-services/scripting/objects/skippedlevelscolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)または[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[UnaryOperatorColumn](../../../analysis-services/scripting/objects/unaryoperatorcolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)または[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)、 [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)、または[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)または[InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[[Namecolumn]](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[ForeignKeyColumn](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md)|**ソース**の要素、 **DataItem**型でなければなりません[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DataItem>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
