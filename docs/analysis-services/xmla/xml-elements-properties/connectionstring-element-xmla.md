---
title: "ConnectionString 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ConnectionString Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6c6227db17c74b4c33d07abfcd809ae01bc3a9a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="connectionstring-element-xmla"></a>ConnectionString 要素 (XMLA)
  親によって使用される接続文字列を含む[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)または[ソース](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|次の表を参照してください。|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1 : 必須要素で、1 回だけ出現します|  
|[ソース](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)、[ソース](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **場所**、要素、 **ConnectionString**要素にはによって使用される接続文字列が含まれています、**復元**または**同期**ローカル データ ソースを更新するか、リモート インスタンスに接続するコマンドです。  
  
 **ソース**、要素、 **ConnectionString**要素にはによって使用される接続文字列が含まれています、**同期**ソース インスタンスに接続するコマンド。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期 (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>参照  
 [要素 &#40; を復元します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [要素 &#40; を同期します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

