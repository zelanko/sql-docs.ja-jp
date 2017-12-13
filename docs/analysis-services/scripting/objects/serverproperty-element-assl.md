---
title: "ServerProperty 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
apiname: ServerProperty Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SERVERPROPERTY
helpviewer_keywords: ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0235ff0306cdc22249f1be7b2a93a4eb93ccc37e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="serverproperty-element-assl"></a>ServerProperty 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]関連付けられているサーバーのプロパティを定義、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ServerProperties>  
   <ServerProperty>  
      <Name>...</Name>  
      <Value>...</Value>  
            <RequiresRestart>...</RequiresRestart>  
            <PendingValue>...</PendingValue>  
      <DefaultValue>...</DefaultValue>  
      <DisplayFlag>...</DisplayFlag>  
   </ServerProperty>  
</ServerProperties>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)|  
|子要素|[DefaultValue](../../../analysis-services/scripting/properties/defaultvalue-element-assl.md)、 [DisplayFlag](../../../analysis-services/scripting/properties/displayflag-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [PendingValue](../../../analysis-services/scripting/properties/pendingvalue-element-assl.md)、 [RequiresRestart](../../../analysis-services/scripting/properties/requiresrestart-element-assl.md)、[値](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **ServerProperty**要素は、データとのインスタンスに関連付けられているサーバー プロパティのメタデータについて説明します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 Analysis Services スクリプト言語 (ASSL)、その他のコレクションに含まれる要素とは異なり、 **ServerProperty**要素は明示的に名前付きの要素ではなく名前/値ペアを使用してサーバーのプロパティを記述します。 名前と値のペアによって、柔軟性および拡張性が得られます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ServerProperty>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
