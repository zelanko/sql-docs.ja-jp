---
title: "要素 (XMLA) の処理 |Microsoft ドキュメント"
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
apiname:
- Process Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Process
- http://schemas.microsoft.com/analysisservices/2003/engine#Process
- microsoft.xml.analysis.process
helpviewer_keywords:
- Process command
ms.assetid: 886fd480-c0e6-4c9b-b65e-da47f874d938
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f43c4c74e23df3b5a81c5497ef356401e70b8479
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="process-element-xmla"></a>Process 要素 (XMLA)
  上のオブジェクトを処理する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Process>  
      <Type>...</Type>  
      <Object>...</Object>  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <WriteBackTableCreation>...</WriteBackTableCreation>  
   </Process>  
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
|子要素|[バインド](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md)、[データソース](../../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md)、 [DataSourceView](../../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md)、 [ErrorConfiguration](../../../analysis-services/xmla/xml-elements-properties/errorconfiguration-element-xmla.md)、[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、[型要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/type-element-xmla.md)、 [WriteBackTableCreation](../../../analysis-services/xmla/xml-elements-properties/writebacktablecreation-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 オブジェクトの処理の詳細については、次を参照してください。[オブジェクトの処理 & #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md).  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

