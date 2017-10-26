---
title: "Capability 要素 (XMLA) |Microsoft ドキュメント"
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
- Capability Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 50a1509e5b4b51778e329dec7bea9554cfca4234
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="capability-element-xmla"></a>Capability 要素 (XMLA)
  親のプロトコル機能のサポートを示す[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)ヘッダー要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **機能**要素は、バイナリや圧縮など、特定の機能が含まれているか、アプリケーションでサポートされていることを示します、 **ProtocolCapabilities**ヘッダー要素で、SOAP ヘッダー、SOAP 要求のまたはのインスタンスによって[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]含まれている、 **ProtocolCapabilities** SOAP 応答の SOAP ヘッダー内のヘッダー要素。 値、**機能**要素は、サポートされる機能の名前。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、以下の表に示す機能がサポートされます。  
  
|機能名|Description|  
|---------------------|-----------------|  
|sx|バイナリ XML サポート|  
|xpress|圧縮サポート|  
  
## <a name="see-also"></a>参照  
 [管理接続およびセッション (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

