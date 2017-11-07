---
title: "Property 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: f0770c5e-6420-4d0c-a5bf-b94eaf6877ca
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d61770b935ad397d5d0db48a3651f143ebef5522
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="property-element-csdlbi"></a>Property 要素 (CSDLBI)
  CSDLBI の Property 要素は、ビジネス インテリジェンス データ モデルをサポートするために、CSDL の Property 要素に追加項目を加えた複合型です。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、CSDLBI Property 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|目次|不可|要求の LCID を含む文字列。|  
|DefaultAggregationFunction|はい|計算が属性上で実行され、他の関数が指定されていない場合に使用される集計関数を指定する文字列。<br /><br /> 指定されない場合、モデルに対する既定の集計関数が使用されます。通常 SUM です。|  
|GroupingBehavior|不可|クエリ結果をグループ化する方法を指定する値。 属性の内容は TGroupingBehavior 単純型によって定義されます (次の表を参照してください)。|  
|OrderBy|不可|このプロパティの値の並べ替え順序が定義されているモデル内の別のプロパティへの参照。<br /><br /> 2 つのプロパティの値は 1 対 1 のマッピングである必要があります。 それ以外の場合は、並べ替えの動作が未定義です。<br /><br /> この要素が省略されると、プロパティは値を基準にして並べ替えられます。|  
|Stability|不可|更新操作の間のプロパティ値の安定性を指定する属性です。<br /><br /> この属性はユーザーが設定するのではなく、デザイン時環境に不安定な値対してのみ発せられます。 行番号を持つ列と、不確定な結果を生成する NOW() または RAND() の式を含む列に常に適用されます。<br /><br /> この属性の値は、Stability 単純型を説明する下記の表で示します。|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 次の表に GroupingBehavior 単純型の値を示します。  
  
|値|Description|  
|-----------|-----------------|  
|GroupOnValue|属性の値によるグループ化。|  
|GroupOnEntityKey|エンティティ キーによるグループ化。|  
  
 この 2 つの値は次のように使用できます。 たとえば、名前で指定される特定のユーザーの給与天引き額を返すクエリがあるとします。 さらにデータベースには、同名で異なるデータベース ID を持つ 2 人のユーザーが含まれているとします。この場合、どちらの属性値が列に適用されているかによって、クエリ結果が異なります。  
  
-   **GroupOnValue**: クエリ結果には、合計、両方のユーザーの給与天引き額が含まれます。  
  
-   **GroupOnEntityKey**: クエリ結果が表示されているが、各ユーザーの給与天引き額には個別に含まれます。  
  
## <a name="stability"></a>Stability  
 次の表の値、**安定性**単純型です。  
  
|値|Description|  
|-----------|-----------------|  
|Stable|更新操作の間、プロパティは一定です。|  
|RowNumber|プロパティに行番号が含まれます。|  
|Volatile|更新操作の間、プロパティが一定ではない場合があります。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 次の XML は、AdventureWorks のテーブル モデル サンプルで使用されているプロパティの一部を CSDLBI Version 1.1 で表現したものです。  
  
```  
  
<EntityType   
   Name="DimEmployee">  
   <Key>  
      <PropertyRef   
      Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber" />  
   </Property>  
  
   <Property   
      Name="EmployeeKey"   
      Type="Int64">  
   <bi:Property />  
   </Property>  
….  
</bi:EntityType>  
</EntityType>  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例では、Contoso Operations キューブを表すデータ モデルにおける列のプロパティの一部を示します。 プレゼンテーション層で特殊な処理が必要な場合を除き、BI 注釈がほとんどの列で必須ではなく、適用もされないことに注目してください。  
  
```  
  
<EntityType   
   Name="Bike">  
  
   <Key>  
      <PropertyRef Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber"   
   />  
   </Property>  
  
   <Property   
      Name="ProductAlternateKey"   
      Type="String"   
      MaxLength="Max"   
      Unicode="true"   
      FixedLength="false">  
   <bi:Property />  
   </Property>  
  
```  
  
## <a name="see-also"></a>参照  
 [CSDL への BI 注釈のテクニカル リファレンス](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  

