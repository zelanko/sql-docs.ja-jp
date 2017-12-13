---
title: "NamingTemplate 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
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
apiname: NamingTemplate Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: NamingTemplate
helpviewer_keywords: NamingTemplate element
ms.assetid: d68d765c-f012-40c1-acd4-32741ee2eadf
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 07ef827685df902c88bd14e35c99dd5dab440149
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="namingtemplate-element-assl"></a>NamingTemplate 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]構築された親子階層におけるレベルの名前付け方法を定義、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)親要素です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <NamingTemplate>...</NamingTemplate>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **NamingTemplate**要素は親属性によってのみ使用 (つまり、他の値、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)の要素、 **DimensionAttribute**親要素設定されている*親*)。  
  
 親属性を使用して階層を構築する際、階層のレベルは親属性に含まれるメンバー間の親子関係により決まります。 したがって、他のディメンションとは異なり、階層に使用されている属性名からレベル名を得ることはできません。  
  
 その代わりに、名前付けテンプレートを使用して親子階層のレベル名を生成します。 **NamingTemplate**親属性で定義された要素には、レベル名を定義するための文字列式が含まれています。 親属性の名前付けテンプレートを定義するには、 名前付けパターンを作成するか、名前の一覧を指定します。  
  
 名前付けパターンには、新しい深い階層レベルの名前に増分しながら挿入されるカウンターのプレースホルダー文字としてアスタリスク (`*`) が含まれています。 たとえば、"(すべて)" レベルが定義されていない場合、`Level *` を使用すると、レベル名 `Level 01`、`Level 02`、`Level 03` が生成されます。 名前付けパターンにプレースホルダー文字が使用されていない場合、最初のレベルにはパターンがそのまま使用され、以降のレベルはパターンの末尾にスペースと番号を追加した名前になります。 たとえば、`Level` を使用すると、レベル名 `Level`、`Level 01`、`Level 02` が生成されます。  
  
 名前付けの値の名前の特定のセットを使用して、 **NamingTemplate**要素がセミコロンで区切られた一連のレベル名に設定します。 一覧に含まれるそれぞれの名前が、以降のレベル名に使用されます。 一覧の名前の数よりもレベルの数が多い場合、超過分のレベル名には一覧の最後の名前がテンプレートとして使用されます。その場合、先に説明したように、最後の名前の末尾にスペースと番号を追加した名前が使用されます。 たとえば、`Division;Group;Unit` を使用すると、レベル名 `Division`、`Group`、`Unit`、`Unit 01`、および `Unit 02` が生成されます。 これに対し、`Division;Group;Unit *` を使用すると、レベル名 `Division`、`Group`、`Unit 03`、および `Unit 04` が生成されます。  
  
 一覧に含まれる名前は、レベル名の一意性を確保するためのテンプレートとして扱われます。 たとえば、`Manager;Team Lead;Manager;Team Lead;Worker *` を使用すると、レベル名 `Manager`、`Team Lead`、`Manager 01`、`Team Lead 01`、`Worker 05`、`Worker 06` が生成されます。  
  
 2 つのアスタリスク (*) を使用して、アスタリスクを含める (\*) レベルの名前、名前付けテンプレートの一部として文字です。  
  
 親に対応する要素**NamingTemplate**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [NamingTemplateTranslations 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)   
 [DimensionAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
