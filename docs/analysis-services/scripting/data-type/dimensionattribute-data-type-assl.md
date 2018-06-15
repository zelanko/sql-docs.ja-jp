---
title: DimensionAttribute データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ecc12dfb1b3ed5c3f8d7ee10bb00e570b779b935
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036663"
---
# <a name="dimensionattribute-data-type-assl"></a>DimensionAttribute データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ディメンション内の属性を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <Type>...</Type>  
   <Usage>...</Usage>  
   <Source>...</Source>  
   <EstimatedCount>...</EstimatedCount>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <ValueColumn>...</ValueColumn>  
   <Translations>...</Translations>  
   <AttributeRelationships>...</AttributeRelationships>  
   <DiscretizationMethod>...</DiscretizationMethod>  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   <RootMemberIf>...</RootMemberIf>  
   <OrderBy>...</OrderBy>  
   <DefaultMember>...</DefaultMember>  
   <OrderByAttributeID>...</OrderByAttributeID>  
   <SkippedLevelsColumn>...</SkippedLevelsColumn>  
   <NamingTemplate>...</NamingTemplate>  
   <MembersWithData>...</MembersWithData>  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   <NamingTemplateTranslations>...</NamingTemplateTranslations>  
   <CustomRollupColumn>...</CustomRollupColumn>  
   <CustomRollupPropertiesColumn>...</CustomRollupPropertiesColumn>  
   <UnaryOperatorColumn>...</UnaryOperatorColumn>  
   <AttributeHierarchyOrdered>...</AttributeHierarchyOrdered>  
   <MemberNamesUnique>...</MemberNamesUnique>  
   <IsAggregatable>...</IsAggregatable>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <AttributeHierarchyDisplayFolder>...</AttributeHierarchyDisplayFolder>  
   <KeyUniquenessGuarantee>...<KeyUniquenessGuarantee>  
   <InstanceSelection>...</InstanceSelection>  
   <Annotations>...</Annotations>  
</DimensionAttribute>  
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
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [AttributeHierarchyDisplayFolder](../../../analysis-services/scripting/properties/attributehierarchydisplayfolder-element-assl.md)、 [AttributeHierarchyEnabled](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md)、 [AttributeHierarchyOptimizedState](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md)、 [AttributeHierarchyOrdered](../../../analysis-services/scripting/properties/attributehierarchyordered-element-assl.md)、 [AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md)、 [AttributeRelationships](../../../analysis-services/scripting/collections/attributerelationships-element-assl.md)、 [CustomRollupColumn](../../../analysis-services/scripting/objects/customrollupcolumn-element-assl.md)、 [CustomRollupPropertiesColumn](../../../analysis-services/scripting/objects/customrolluppropertiescolumn-element-assl.md)、 [DefaultMember](../../../analysis-services/scripting/properties/defaultmember-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [DiscretizationBucketCount](../../../analysis-services/scripting/properties/discretizationbucketcount-element-assl.md)、 [DiscretizationMethod](../../../analysis-services/scripting/properties/discretizationmethod-element-assl.md)、 [EstimatedCount](../../../analysis-services/scripting/properties/estimatedcount-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[InstanceSelection](../../../analysis-services/scripting/properties/instanceselection-element-assl.md)、 [IsAggregatable](../../../analysis-services/scripting/properties/isaggregatable-element-assl.md)、 [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)、 [KeyUniquenessGuarantee](../../../analysis-services/scripting/properties/keyuniquenessguarantee-element-assl.md)、 [MemberNamesUnique](../../../analysis-services/scripting/properties/membernamesunique-element-assl.md)、 [MembersWithData](../../../analysis-services/scripting/properties/memberswithdata-element-assl.md)、 [MembersWithDataCaption](../../../analysis-services/scripting/properties/memberswithdatacaption-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)、 [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)、 [NamingTemplateTranslations](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)、 [OrderBy](../../../analysis-services/scripting/properties/orderby-element-assl.md)、 [OrderByAttributeID](../../../analysis-services/scripting/properties/orderbyattributeid-element-assl.md)、 [RootMemberIf](../../../analysis-services/scripting/properties/rootmemberif-element-assl.md)、 [SkippedLevelsColumn](../../../analysis-services/scripting/objects/skippedlevelscolumn-element-assl.md)、 [ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[型](../../../analysis-services/scripting/properties/type-element-dimensionattribute-assl.md)、 [UnaryOperatorColumn](../../../analysis-services/scripting/objects/unaryoperatorcolumn-element-assl.md)、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)、 [ValueColumn](../../../analysis-services/scripting/objects/valuecolumn-element-assl.md)|  
|派生要素|[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)([属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)のコレクション[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 DeploymentMode 構成プロパティの値を 1 および 2 で、サービスを実行する場合、次の制限が適用されます (SharePoint モードおよび表形式モードを実行するために使用[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]およびテーブル モデル データベース)。  
  
-   Usage 要素に使用できる値は KEY または REGULAR のみとなります。  
  
-   IsAggregatable 要素を False に設定することはできません。  
  
-   OrderBy 要素に使用できる値は KEY または PROPERTYKEY のみとなります。  
  
-   計算列をテーブルの主キーにすることはできません。  
  
-   計算列のバインドに DataSize を含めることはできません。  
  
-   属性の定義を保存する前に、各計算列の構文検証が実行されます。  
  
-   AttributeRelationships については、RelationshipType の値を Flexible に設定する必要があります。  
  
-   'RowNumber' によって識別される属性 'RowNumber' には、整数型が割り当てられている必要があります。  
  
-   RowNumberBinding 型の KeyBinding を割り当てることができるのは 'RowNumber' 属性だけです。  
  
-   'RowNumber' を除くすべての属性は、キーに関連した基数が 1 になります (属性そのものがキーである場合を除く)。  
  
-   OrderBy によって指定された列が PropertyKey でもある場合、OrderByAttributeId が行番号列を指し示すことはできません。  
  
-   キーとして使用されている属性は、他のすべての属性に関連している必要があります。他の種類のリレーションシップはサポートされていません。  
  
-   NullProcessing 要素を 'UnknownMember' に設定することはできません。  
  
-   バインドを 'Value' に設定することはできません。  
  
 DeploymentMode 構成プロパティの値を 1 および 2 で、サービスを実行するときに、次の要素はサポートされていません (SharePoint モードおよび表形式モードを実行するために使用[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]およびテーブル モデル データベース)。  
  
-   AttributeHierarchyOptimizedState  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   DefaultMember  
  
-   DiscretizationBucketCount  
  
-   DiscretizationMethod  
  
-   SkippedLevelsColumn  
  
-   Source  
  
-   UnaryOperatorColumn  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
