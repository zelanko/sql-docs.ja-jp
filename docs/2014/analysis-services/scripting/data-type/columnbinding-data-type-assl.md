---
title: ColumnBinding データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ColumnBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnBinding
helpviewer_keywords:
- ColumnBinding data type
ms.assetid: 3ab1bac1-6716-4b17-a107-d5f9c744c5e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 271b4ae8b305e554f94bd1b0da3bbed96a7dd476
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149342"
---
# <a name="columnbinding-data-type-assl"></a>ColumnBinding データ型 (ASSL)
  データ ソース ビュー内の列のバインドを表す派生データ型を定義、 [DataItem](dataitem-data-type-assl.md)要素。  
  
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
|基本データ型|[バインド](binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ColumnID](../properties/columnid-element-eventcolumn-assl.md)、 [TableID](../properties/id-element-assl.md)|  
|派生要素|参照してください[バインド](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 有効な XML の要素名を作成する[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]`DataSet`オブジェクトは、XML スキーマ定義 (XSD) にシリアル化するときにテーブル名をエンコード; たとえば、名"Order Details"が"Order_x0020_Details"になります。 同様に、`ColumnID` 要素に含まれており、データ ソース ビュー (DSV) のオブジェクトを参照する `TableID` 要素と `ColumnBinding` 要素も、シリアル化のときに名前が DSV 内のテキストに一致するように、名前をエンコードする必要があります。 Analysis Services インスタンスでは、`DataSet` オブジェクト モデルと同様に、これらの名前をデコードします。  
  
 `TableDefinitions` データ型を使用しており、DSV 内のテーブルを参照する要素に含まれている `TableBinding` 要素も、XSD へのシリアル化のときに名前をエンコードする必要があります。 ただし、`Partition` バインド内のテーブル名はエンコードしないでください。これらの名前はデータベースに存在するテーブル名にすぎず、DSV に存在する必要はないためです。 `Partition` バインド内のテーブル名をエンコードしないことで、次の目的も達成されます。  
  
-   パーティションのデータ定義ライブラリ (DDL) がより簡潔に保たれます。  
  
-   パーティションにはテーブル名と SELECT ステートメントのどちらかを含めることができ、SELECT ステートメントはエンコードする必要がないので、一貫性が向上します。  
  
 テーブル名と列名に区切り記号 ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の場合は "[" など) が含まれません。  
  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、`Binding`型との継承階層`Binding`型を参照してください[&#40;ASSL&#41;](binding-data-type-assl.md)します。  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 AMO オブジェクト モデルの対応する要素は <xref:Microsoft.AnalysisServices.ColumnBinding> です。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
