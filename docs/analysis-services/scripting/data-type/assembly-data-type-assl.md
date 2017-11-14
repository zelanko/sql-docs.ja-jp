---
title: "Assembly データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Assembly Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Assembly data type
ms.assetid: 0a381322-9509-4579-a754-c6cdd0a70cc9
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 98d9240e9f0c8ff2ab4a655676beba08af24265d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="assembly-data-type-assl"></a>Assembly データ型 (ASSL)
  表す抽象プリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリまたは COM ダイナミック リンク ライブラリ (DLL) に関連付けられている、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)または[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
> [!IMPORTANT]  
>  COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、 [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]では、COM アセンブリが推奨されていません。 COM アセンブリは、今後のリリースではサポートされない可能性があります。  
  
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
|派生データ型|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)、 [ComAssembly](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [ImpersonationInfo](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、[名](../../../analysis-services/scripting/properties/name-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 **アセンブリ**データ型の基本データ型は、 **ComAssembly**インスタンスまたはデータベースに関連付けられた COM ライブラリを表す要素および**ClrAssembly**を表す要素は、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]インスタンスまたはデータベースに関連付けられているアセンブリ。 アセンブリの詳細については、次を参照してください。[多次元モデルのアセンブリの管理](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Assembly>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Database 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

