---
title: "Detach 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Detach command
ms.assetid: adbc7920-2a4a-4842-9e6f-37006fa19ff8
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7ec8a5cfc27be9fbf9fcf4f5844cb0112ad437cd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="detach-element"></a>Detach 要素
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースを現在のサーバー インスタンスからデタッチします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Detach>  
      <Object>...</Object>  
      <Password>...</Password>  
   </Detach>  
</Command>  
  
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
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)<br /><br /> [Password](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Attach 要素](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [アタッチし、Analysis Services データベースのデタッチ](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [データベースの Readwritemode](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  

