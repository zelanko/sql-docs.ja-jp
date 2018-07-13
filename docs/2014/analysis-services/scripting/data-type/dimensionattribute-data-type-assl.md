---
title: DimensionAttribute データ型 (ASSL) |Microsoft Docs
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
- DimensionAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionAttribute
helpviewer_keywords:
- DimensionAttribute data type
ms.assetid: 94349a87-b284-49d1-ac72-888f0375ceb8
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9e07d7b7c313c4d9d21e8e562f2ed6893a08b42
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194292"
---
# <a name="dimensionattribute-data-type-assl"></a>DimensionAttribute データ型 (ASSL)
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
|子要素|[注釈](../collections/annotations-element-assl.md)、 [AttributeHierarchyDisplayFolder](../properties/displayfolder-element-assl.md)、 [AttributeHierarchyEnabled](../properties/enabled-element-assl.md)、 [AttributeHierarchyOptimizedState](../properties/state-element-assl.md)、 [AttributeHierarchyOrdered](../properties/attributehierarchyordered-element-assl.md)、 [AttributeHierarchyVisible](../properties/visible-element-assl.md)、 [AttributeRelationships](../collections/relationships-element-assl.md)、 [CustomRollupColumn](../objects/column-element-assl.md)、 [CustomRollupPropertiesColumn](../objects/customrolluppropertiescolumn-element-assl.md)、 [DefaultMember](../objects/member-element-assl.md)、[説明](../properties/description-element-assl.md)、 [DiscretizationBucketCount](../properties/discretizationbucketcount-element-assl.md)、 [DiscretizationMethod](../properties/discretizationmethod-element-assl.md)、 [EstimatedCount](../properties/estimatedcount-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [InstanceSelection](../properties/instanceselection-element-assl.md)、 [IsAggregatable](../properties/isaggregatable-element-assl.md)、[KeyColumns](../collections/columns-element-assl.md)、 [KeyUniquenessGuarantee](../properties/keyuniquenessguarantee-element-assl.md)、 [MemberNamesUnique](../properties/membernamesunique-element-assl.md)、 [MembersWithData](../objects/data-element-assl.md)、 [MembersWithDataCaption](../properties/caption-element-assl.md)、[名前](../properties/name-element-assl.md)、 [NameColumn](../objects/namecolumn-element-assl.md)、 [NamingTemplate](../properties/namingtemplate-element-assl.md)、 [NamingTemplateTranslations](../collections/translations-element-assl.md)、 [OrderBy](../properties/orderby-element-assl.md)、 [OrderByAttributeID](../properties/attributeid-element-assl.md)、 [RootMemberIf](../properties/rootmemberif-element-assl.md)、 [SkippedLevelsColumn](../objects/skippedlevelscolumn-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)、[翻訳](../collections/translations-element-assl.md)、[型](../properties/type-element-dimensionattribute-assl.md)、 [UnaryOperatorColumn](../objects/unaryoperatorcolumn-element-assl.md)、[使用状況](../properties/usage-element-dimensionattribute-assl.md)、 [ValueColumn](../objects/valuecolumn-element-assl.md)|  
|派生要素|[属性](../objects/attribute-element-assl.md)([属性](../collections/attributes-element-assl.md)のコレクション[ディメンション](../objects/dimension-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 DeploymentMode 構成プロパティの値を 1 および 2 (PowerPivot データベースおよびテーブル モデル データベースを実行するために使用される SharePoint モードおよび表形式モード) としてサービスが実行されている場合、次の制限が適用されます。  
  
-   Usage 要素に使用できる値は KEY または REGULAR のみとなります。  
  
-   IsAggregatable 要素を False に設定することはできません。  
  
-   OrderBy 要素に使用できる値は KEY または PROPERTYKEY のみとなります。  
  
-   計算列をテーブルの主キーにすることはできません。  
  
-   計算列のバインドに DataSize を含めることはできません。  
  
-   属性の定義を保存する前に、各計算列の構文検証が実行されます。  
  
-   AttributeRelationships については、RelationshipType の値を Flexible に設定する必要があります。  
  
-   'RowNumber' によって識別される属性 'RowNumber' には、整数型が割り当てられている必要があります。  
  
-   RowNumberBinding 型の KeyBinding を割り当てることができるのは 'RowNumber' 属性だけです。  
  
-   'RowNumber' を除くすべての属性は、キーに関連したカーディナリティが 1 になります (属性そのものがキーである場合を除く)。  
  
-   OrderBy によって指定された列が PropertyKey でもある場合、OrderByAttributeId が行番号列を指し示すことはできません。  
  
-   キーとして使用されている属性は、他のすべての属性に関連している必要があります。他の種類のリレーションシップはサポートされていません。  
  
-   NullProcessing 要素を 'UnknownMember' に設定することはできません。  
  
-   バインドを 'Value' に設定することはできません。  
  
 DeploymentMode 構成プロパティの値を 1 および 2 (PowerPivot データベースおよびテーブル モデル データベースを実行するために使用される SharePoint モードおよび表形式モード) としてサービスが実行されている場合、次の要素はサポートされません。  
  
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
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
