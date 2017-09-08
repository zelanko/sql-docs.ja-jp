---
title: "Assembly 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Assembly Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ASSEMBLY
helpviewer_keywords:
- Assembly element [ASSL]
ms.assetid: 1910ccb0-7da0-4ee1-9548-ad6e0068d23d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 45a9b1386f225021c3500b9a5dc3d9d400c3021f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="assembly-element-assl"></a>Assembly 要素 (ASSL)
  表す、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリまたは COM ダイナミック リンク ライブラリ (DLL) に関連付けられている、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素または[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Assemblies>  
   <Assembly xsi:type="ClrAssembly">...</Assembly>  
   <!-- or -->  
   <Assembly xsi:type="ComAssembly">...</Assembly>  
</Assemblies>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)、 [ComAssembly](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アセンブリ](../../../analysis-services/scripting/collections/assemblies-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Assembly>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Database 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
