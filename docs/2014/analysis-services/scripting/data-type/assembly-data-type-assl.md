---
title: Assembly データ型 (ASSL) |Microsoft Docs
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
- Assembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Assembly data type
ms.assetid: 0a381322-9509-4579-a754-c6cdd0a70cc9
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 40cafd0d8ef11feaebce5161e97ef3717a9fb943
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233832"
---
# <a name="assembly-data-type-assl"></a>Assembly データ型 (ASSL)
  表す抽象プリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリまたは COM ダイナミック リンク ライブラリ (DLL) に関連付けられている、 [Server](../objects/server-element-assl.md)または[データベース](../objects/database-element-assl.md)要素。  
  
> [!IMPORTANT]  
>  COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、[!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)] では、COM アセンブリが非推奨とされました。 COM アセンブリは、今後のリリースではサポートされない可能性があります。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Assembly>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Annotations>...</Annotations>  
</Assembly>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[ClrAssembly](assembly-data-type-assl.md)、 [ComAssembly](comassembly-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、[説明](../properties/description-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [ImpersonationInfo](../properties/impersonationinfo-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、[名](../properties/name-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Assembly` データ型は、インスタンスまたはデータベースに関連付けられた COM ライブラリを表す `ComAssembly` 要素と、インスタンスまたはデータベースに関連付けられた [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] アセンブリを表す `ClrAssembly` 要素の基本データ型になります。 アセンブリの詳細については、次を参照してください。[多次元モデルのアセンブリの管理](../../multidimensional-models/multidimensional-model-assemblies-management.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Assembly>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素&#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Database 要素&#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
