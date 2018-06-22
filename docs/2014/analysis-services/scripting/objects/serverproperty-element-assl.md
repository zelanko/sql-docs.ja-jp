---
title: ServerProperty 要素 (ASSL) |Microsoft ドキュメント
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
- ServerProperty Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SERVERPROPERTY
helpviewer_keywords:
- ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6cb62681b0c25c83d54076a67a37addc764102da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072851"
---
# <a name="serverproperty-element-assl"></a>ServerProperty 要素 (ASSL)
  関連付けられているサーバーのプロパティを定義、[サーバー](server-element-assl.md)要素。  
  
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
|親要素|[ServerProperties](../collections/serverproperties-element-assl.md)|  
|子要素|[DefaultValue](../properties/value-element-assl.md)、 [DisplayFlag](../properties/displayflag-element-assl.md)、[名前](../properties/name-element-assl.md)、 [PendingValue](../properties/pendingvalue-element-assl.md)、 [RequiresRestart](../properties/requiresrestart-element-assl.md)、[値](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 `ServerProperty`要素は、データとのインスタンスに関連付けられているサーバー プロパティのメタデータについて説明します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 Analysis Services スクリプト言語 (ASSL) の他のコレクションに含まれている要素とは異なり、`ServerProperty` 要素では、明示的に名前を付けられた要素の代わりに名前と値のペアを使用してサーバー プロパティを記述します。 名前と値のペアによって、柔軟性および拡張性が得られます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ServerProperty>します。  
  
## <a name="see-also"></a>参照  
 [サーバー要素&#40;ASSL&#41;](server-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  