---
title: Hierarchy データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Hierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Hierarchy data type
ms.assetid: 2e05917e-7e5d-4dd1-817b-4ff5647747ff
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8bce652f4fcb0453606ecfa2b2f23796f55d399c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199962"
---
# <a name="hierarchy-data-type-assl"></a>Hierarchy データ型 (ASSL)
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
|子要素|[AllMemberName](../properties/name-element-assl.md)、 [AllMemberTranslations](../collections/translations-element-assl.md)、 [AllowDuplicateNames](../properties/allowduplicatenames-element-assl.md)、 [Annotations](../collections/annotations-element-assl.md)、 [Description](../properties/description-element-assl.md)、 [DisplayFolder](../properties/displayfolder-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [Levels](../collections/levels-element-assl.md)、 [MemberNamesUnique](../properties/membernamesunique-element-assl.md)、 [Name](../properties/name-element-assl.md)、 [Translations](../collections/translations-element-assl.md)|  
|派生要素|[Hierarchy](../objects/hierarchy-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 *MemberNamesUnique* 要素は、DevelopmentMode 1 または 2 (それぞれ、SharePoint サーバー モードまたはテーブル サーバー モード) ではサポートされません。  
  
 *MemberKeysUnique* 要素は、DevelopmentMode 1 または 2 (それぞれ、SharePoint サーバー モードまたはテーブル サーバー モード) ではサポートされません。  
  
 *AllowDuplicateNames* 要素は、DevelopmentMode 1 または 2 (それぞれ、SharePoint サーバー モードまたはテーブル サーバー モード) ではサポートされません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Hierarchy>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
