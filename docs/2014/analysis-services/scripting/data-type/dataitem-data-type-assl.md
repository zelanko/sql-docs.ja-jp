---
title: DataItem データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f16c23941fc1048429ced974b88bba378bc72c2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153482"
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
  
## <a name="remarks"></a>Remarks  
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
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[NameColumn](../objects/namecolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/foreignkeycolumn-element-assl.md)|`Source` 要素、`DataItem`型でなければなりません[ColumnBinding](binding-data-type-assl.md)|  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DataItem>します。  
  
## <a name="see-also"></a>関連項目  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
