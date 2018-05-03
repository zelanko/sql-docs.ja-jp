---
title: Hierarchy データ型 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Hierarchy Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Hierarchy data type
ms.assetid: 2e05917e-7e5d-4dd1-817b-4ff5647747ff
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a9c5a8a1d181e27e36d4a408b1a46601865448f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="hierarchy-data-type-assl"></a>Hierarchy データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ディメンション内の階層を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Hierarchy>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Translations>...</Translations>  
   <AllMemberName>...</AllMemberName>  
   <AllMemberTranslations>...</AllMemberTranslation>  
   <MemberNamesUnique>...</MemberNamesUnique>  
   <AllowDuplicateNames>...</AllowDuplicateNames>  
   <Levels>...</Levels>  
   <Annotations>...</Annotation>  
</Hierarchy>  
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
|子要素|[AllMemberName](../../../analysis-services/scripting/properties/allmembername-element-assl.md)、 [AllMemberTranslations](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md)、 [AllowDuplicateNames](../../../analysis-services/scripting/properties/allowduplicatenames-element-assl.md)、 [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [Description](../../../analysis-services/scripting/properties/description-element-assl.md)、 [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [Levels](../../../analysis-services/scripting/collections/levels-element-assl.md)、 [MemberNamesUnique](../../../analysis-services/scripting/properties/membernamesunique-element-assl.md)、 [Name](../../../analysis-services/scripting/properties/name-element-assl.md)、 [Translations](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|派生要素|[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 *MemberNamesUnique* 要素は、DevelopmentMode 1 または 2 (それぞれ、SharePoint サーバー モードまたはテーブル サーバー モード) ではサポートされません。  
  
 *MemberKeysUnique* 要素は、DevelopmentMode 1 または 2 (それぞれ、SharePoint サーバー モードまたはテーブル サーバー モード) ではサポートされません。  
  
 *AllowDuplicateNames* 要素は、DevelopmentMode 1 または 2 (それぞれ、SharePoint サーバー モードまたはテーブル サーバー モード) ではサポートされません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Hierarchy>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
