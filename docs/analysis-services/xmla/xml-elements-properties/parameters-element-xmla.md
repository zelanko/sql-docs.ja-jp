---
title: "Parameters 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname:
- Parameters Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords:
- Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 27bf966c1a1fb44c547a74f38cc3cddd6399793c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="parameters-element-xmla"></a>Parameters 要素 (XMLA)
  コレクションを格納[パラメーター](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)によって使用される要素、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
 **Namespace:**`urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>構文  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[実行](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|子要素|[パラメーター](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 などのいくつかの XML for Analysis (XMLA) コマンド、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)コマンド、追加情報が必要になることができます。 **パラメーター**要素は、XMLA コマンドのチャンクされた情報を含む、追加の情報を提供するためのメカニズムを提供します。  
  
 XMLA コマンドを使用しない場合、**パラメーター**要素を呼び出すときに、要素を省略することができます、 **Execute**メソッドです。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

