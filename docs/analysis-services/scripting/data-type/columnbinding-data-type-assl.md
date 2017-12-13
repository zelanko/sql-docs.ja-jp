---
title: "ColumnBinding データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ColumnBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ColumnBinding
helpviewer_keywords: ColumnBinding data type
ms.assetid: 3ab1bac1-6716-4b17-a107-d5f9c744c5e6
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fe72c43754a9df628748cedf31472143ec201b1a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="columnbinding-data-type-assl"></a>ColumnBinding データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データ ソース ビュー内の列のバインドを表す派生データ型を定義、 [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ColumnBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
      <ColumnID>...</ColumnID>  
</ColumnBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ColumnID](../../../analysis-services/scripting/properties/columnid-element-eventcolumn-assl.md)、 [TableID](../../../analysis-services/scripting/properties/tableid-element-assl.md)|  
|派生要素|参照してください[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 有効な XML 要素名を作成する[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]**データセット**オブジェクトは、XML スキーマ定義 (XSD) にシリアル化するときにテーブル名をエンコードです。 たとえば、名前"Order Details"は"order_x0020_details"です。 同様に、 **ColumnID**と**TableID**要素に含まれる、 **ColumnBinding**要素とデータ ソース ビュー (DSV) 内のオブジェクトを参照する必要がありますもエンコード名前が、DSV 内のテキストを直接一致するように、シリアル化中に名前です。 Analysis Services インスタンスと同様に、これらの名前をデコードは、**データセット**オブジェクト モデルでは、します。  
  
 A **TableDefinitions**要素を使用して、含まれる要素の**TableBinding**データ型と、DSV 内のテーブルを参照する必要がありますも名前をエンコード XSD にシリアル化するとき。 ただし、テーブル名が、**パーティション**これらの名前は、データベース内に存在し、DSV に存在する必要はありませんテーブルの名前だけであるために、バインドをエンコードする必要があります。 いないテーブル名をエンコードで、**パーティション**バインドも、次を実現します。  
  
-   パーティションのデータ定義ライブラリ (DDL) がより簡潔に保たれます。  
  
-   パーティションにはテーブル名と SELECT ステートメントのどちらかを含めることができ、SELECT ステートメントはエンコードする必要がないので、一貫性が向上します。  
  
 テーブル名と列名に区切り記号 ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の場合は "[" など) が含まれません。  
  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、**バインド**型との継承階層**バインド**型を参照してください[バインドのデータ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとのバインド &#40;です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 AMO オブジェクト モデルの対応する要素は <xref:Microsoft.AnalysisServices.ColumnBinding> です。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
