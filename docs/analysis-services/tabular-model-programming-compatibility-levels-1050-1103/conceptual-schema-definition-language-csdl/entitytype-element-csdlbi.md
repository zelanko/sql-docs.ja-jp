---
title: "EntityType 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 372e2c13-ec38-4bb1-981c-50758d59a1da
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f8eb72bef98a90f45607c8933539a5ee322dea5c
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="entitytype-element-csdlbi"></a>EntityType 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
**EntityType**要素は複合型であり、顧客やデータ モデル内の注文などの高レベルのエンティティの構造体を表します。 **Bi: EntityType**要素の定義を拡張する[EntityType](http://msdn.microsoft.com/library/bb399206.aspx)で使用される、 [Entity Data Framework](http://msdn.microsoft.com/library/bb399567.aspx)です。  
  
 EntityType 要素は、データ モデルに含まれる各エンティティに対して指定される必要があります。 EntityType のサブ要素では、テーブルの列とメジャーが記述されます。 テーブル間のリレーションシップが含まれている、 **EntityContainer**です。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表は、要素と属性を定義する、 **EntityType**要素。 適用される属性を参照しても、 [EntityType](http://msdn.microsoft.com/library/bb399206.aspx)要素。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|目次|いいえ|列内のデータの種類を含む文字列です。 値は、データ モデルの DimensionAttributeTypeEnumType の値から取得されます。<br /><br /> DimensionAttributeTypeEnumType の値が ExtendedType の場合は、Contents の値は DimensionAttribute の ExtendedType 要素から取得されます。 クライアントはこれらの値に対応する必要はありません。|  
|DefaultDetails|いいえ|プロパティ参照のリスト。テーブル内の列のセットを表します。<br /><br /> 参照してください[DefaultDetails 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/defaultdetails-element-csdlbi.md).|  
|DefaultImage|いいえ|エンティティを示すイメージを含む列への参照。<br /><br /> 多次元モデルでは、この要素は、ディメンション属性のバイナリ属性に対応します。 この属性が存在する場合、要素にはただ 1 つの MemberRef 要素が必ず含まれます。<br /><br /> 参照してください[MemberRef 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DefaultMeasure|いいえ|エンティティ上での計算時に既定として使用されるエンティティのメジャーへの参照です。 指定しない場合は、SUM が既定値です。<br /><br /> 参照してください[MemberRef 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DisplayKey|いいえ|列またはロール エンドに対する参照のリスト。エンティティ インスタンスを一意に識別する強い識別子を構成します。<br /><br /> 参照してください[DisplayKey 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/displaykey-element-csdlbi.md).|  
|階層|いいえ|モデルの階層のリスト。<br /><br /> 参照してください[Hierarchy 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).|  
|ReferenceName|はい|Data Analysis Expressions (DAX) クエリでこのエンティティを参照するために使用できる識別子。<br /><br /> この属性が存在しない場合は、エンティティの完全修飾されたフィールド名が使用されます。|  
|SortMembers|いいえ|並べ替えるの基準となるプロパティの一覧です。 SortDirection 属性が昇順または降順を示します。|  
  
## <a name="contents-element"></a>Contents 要素  
 **内容**要素は、エンティティ内のデータの型を記述する単純な型です。  
  
 エンティティ (列) のコンテンツは次の値のいずれかです。  
  
|値|Description|  
|-----------|-----------------|  
|Regular|特に定義されていない場合。|  
|[時刻]|年、半期、四半期、月、日などの時間間隔を表す属性。|  
|Geography|市区町村や郵便番号などの地理情報を表す属性。|  
|Organization|従業員や子会社などの組織情報を表す属性。|  
|BillOfMaterials|製品の部品表などの在庫情報や製造情報を表す属性。|  
|Accounts|財務報告用の勘定科目一覧表を表す属性。|  
|Customers|顧客情報や連絡先情報を表す属性。|  
|Products|製品情報を表す属性。|  
|Scenario|計画的または戦略的な分析情報を表す属性。|  
|Quantitative|量的な情報を表す属性。|  
|Utility|その他の情報を表す属性。|  
|通貨|通貨のデータとメタデータが含まれます。|  
|Rates|通貨レート情報を表す属性。|  
|Channel|チャネル情報を表す属性。|  
|Promotion|マーケティング関連のプロモーション情報を表す属性。|  
  
## <a name="example"></a>例  
 **表形式**  
  
 次の例は、AdventureWorks のテーブル モデルで使用される Geography テーブルの CSDLBI Version 1.1 による表現の一部です。 RowNumber 列が非表示の列をテーブル モデルでの行識別子として自動的に生成され、そのため、内容が属性を持つ**RowNumber**です。  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 次の例は、Contoso Operations キューブからの時間ディメンションの一部を表す、CSDLBI Version 1.1 で表現した EntityType 要素を示します。  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>参照  
 [CSDL への BI 注釈のテクニカル リファレンス](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
