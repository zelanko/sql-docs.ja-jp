---
title: Capability 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Capability Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c6fd189a44ec34283e87cd220f2c582f982ffa9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105342"
---
# <a name="capability-element-xmla"></a>Capability 要素 (XMLA)
  親でプロトコル機能のサポートを示します[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)ヘッダー要素。  
  
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Capability`要素は、バイナリや圧縮などの特定の機能が含まれているか、アプリケーションでサポートされていることを示します、`ProtocolCapabilities`またはのインスタンスによって、SOAP 要求の SOAP ヘッダー内のヘッダー要素[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]に含まれて、 `ProtocolCapabilities` SOAP 応答の SOAP ヘッダー内のヘッダー要素。 `Capability` 要素の値は、サポートされる機能の名前です。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、以下の表に示す機能がサポートされます。  
  
|機能名|説明|  
|---------------------|-----------------|  
|sx|バイナリ XML サポート|  
|xpress|圧縮サポート|  
  
## <a name="see-also"></a>参照  
 [接続およびセッション管理&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
