---
title: Hierarchy データ型 (ASSL) |Microsoft ドキュメント
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
- Hierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Hierarchy data type
ms.assetid: 2e05917e-7e5d-4dd1-817b-4ff5647747ff
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 14354458e3441c6f8f2691350e9236f2aecb6cdd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178560"
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
  
  